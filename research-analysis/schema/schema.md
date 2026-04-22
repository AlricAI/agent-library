---
name: SCHEMA
description: This file is the **authoritative specification** for all database tables.
model: claude-sonnet-4-5
---
# SCHEMA.md — Database Schema Reference

This file is the **authoritative specification** for all database tables. It is the source of truth for:
- `db/schema.sql` (DDL implementation)
- `db/queries.py` (typed query layer)
- Alembic migrations in `db/migrations/`

Any schema change requires updating this file AND creating an Alembic migration.

---

## 1. Overview

The database runs on **TimescaleDB 2.14 / PostgreSQL 16**. All time-series tables are TimescaleDB hypertables partitioned by time. Relational metadata lives in plain PostgreSQL tables.

```
TimescaleDB hypertables (time-partitioned):
  trades              ← raw CLOB tick events
  slot_master         ← one row per resolved market slot  ← PRIMARY ARTEFACT
  oracle_bounds       ← per-slot oracle computation output
  reference_prices    ← BTC/ETH 1-second OHLCV

PostgreSQL tables (relational):
  markets             ← market registry
  resolutions         ← resolution records
  fee_schedules       ← platform fee configs
  break_even_surface  ← weekly break-even p* surface
  stats_results       ← rolling regression output
  mc_run_registry     ← Monte Carlo run metadata
```

---

## 2. Core Hypertable: `slot_master`

The central data artefact. One row per resolved prediction market slot. Written by `pipeline/stages/p3_slots.py`. Read by everything else.

**Hypertable config:**
- Partition column: `t0_utc`
- `chunk_time_interval = INTERVAL '1 day'`
- Compression: enabled after 7 days (`timescaledb.compress`)

```sql
CREATE TABLE slot_master (
    -- Identity
    slot_id              UUID        NOT NULL,           -- SHA-256(platform:market_id:t0_utc) as UUID
    market_id            VARCHAR(64) NOT NULL,           -- Platform-native market identifier
    class_code           CHAR(2)     NOT NULL,           -- C1, C2, P1, P2, E1, E2, M1, M2, S1
    platform             VARCHAR(20) NOT NULL,           -- polymarket | kalshi | manifold | metaculus | betfair

    -- Timing
    t0_utc               TIMESTAMPTZ NOT NULL,           -- Slot open: first trade timestamp
    t_close_utc          TIMESTAMPTZ NOT NULL,           -- Slot resolution timestamp
    t_seconds            INTEGER     NOT NULL,           -- Duration in seconds (≈300 for C1)

    -- Market primitives
    outcome_yes          BOOLEAN     NOT NULL,           -- TRUE = YES token won
    q0_yes               FLOAT8      NOT NULL,           -- Opening mid-price of YES token at t0
    q0_no                FLOAT8      NOT NULL,           -- Opening mid-price of NO token at t0
    q_star_winner        FLOAT8      NOT NULL,           -- Min trade price of winning token during slot
    q_star_ts            TIMESTAMPTZ,                    -- Timestamp of q_star observation
    q_star_alpha         FLOAT4,                         -- Fraction of slot elapsed at q_star_ts

    -- Volume and liquidity
    volume_usd           FLOAT8,                         -- Total USD volume (all tokens, both sides)
    volume_winner_usd    FLOAT8,                         -- USD volume on winning token side
    n_trades             INTEGER,                        -- Total trade count during slot
    depth_bid_2pct_usd   FLOAT8,                         -- USD depth within 2% of q0 on bid side

    -- Volatility
    sigma_q_winner       FLOAT4,                         -- Std dev of winning-token prices during slot
    price_range_winner   FLOAT4,                         -- max - min of winning-token prices

    -- Costs
    fee_rate             FLOAT4      NOT NULL DEFAULT 0.02,  -- Platform fee on gross winnings
    gas_usd              FLOAT4      NOT NULL DEFAULT 0.0,   -- Actual gas cost in USD

    -- Reference price (for C1/C2 only; NULL for others)
    btc_price_open       FLOAT8,                         -- BTC/USDT spot at t0
    btc_price_close      FLOAT8,                         -- BTC/USDT spot at t_close
    btc_return_pct       FLOAT4,                         -- (close/open - 1) * 100

    -- Quality
    data_quality_flag    SMALLINT    NOT NULL DEFAULT 0, -- 0=clean,1=warn,2=dispute,3=exclude
    ingested_at          TIMESTAMPTZ NOT NULL DEFAULT NOW(),

    -- Constraints
    PRIMARY KEY (slot_id, t0_utc),   -- compound PK required by TimescaleDB
    CONSTRAINT chk_q0_range       CHECK (q0_yes BETWEEN 0.001 AND 0.999),
    CONSTRAINT chk_q_star_pos     CHECK (q_star_winner > 0),
    CONSTRAINT chk_q_star_leq_q0  CHECK (q_star_winner <= q0_yes + 0.001), -- +tolerance for floating point
    CONSTRAINT chk_quality_flag   CHECK (data_quality_flag IN (0, 1, 2, 3)),
    CONSTRAINT chk_class_code     CHECK (class_code IN ('C1','C2','P1','P2','E1','E2','M1','M2','S1')),
    CONSTRAINT chk_platform       CHECK (platform IN ('polymarket','kalshi','manifold','metaculus','betfair','predictit'))
);

SELECT create_hypertable('slot_master', 't0_utc', chunk_time_interval => INTERVAL '1 day');

CREATE INDEX idx_slot_master_class_time ON slot_master (class_code, t0_utc DESC);
CREATE INDEX idx_slot_master_market     ON slot_master (market_id, t0_utc DESC);
CREATE INDEX idx_slot_master_quality    ON slot_master (data_quality_flag) WHERE data_quality_flag = 0;
```

### slot_id Computation

```python
import hashlib, uuid

def compute_slot_id(platform: str, market_id: str, t0_utc: datetime) -> uuid.UUID:
    raw = f"{platform}:{market_id}:{t0_utc.isoformat()}"
    digest = hashlib.sha256(raw.encode()).hexdigest()
    return uuid.UUID(digest[:32])  # truncate to 128 bits for UUID type
```

**This must be deterministic.** The same inputs always produce the same `slot_id`. Re-ingesting a slot upserts, never duplicates.

---

## 3. `trades` Hypertable

Raw CLOB tick events. Written by P1 ingestion. Read only by P3 (slot constructor). Compressed after 7 days.

```sql
CREATE TABLE trades (
    trade_id        VARCHAR(128) NOT NULL,   -- Platform-native trade/fill ID
    market_id       VARCHAR(64)  NOT NULL,
    platform        VARCHAR(20)  NOT NULL,
    ts_utc          TIMESTAMPTZ  NOT NULL,   -- Trade timestamp
    token           VARCHAR(3)   NOT NULL,   -- 'yes' | 'no'
    side            VARCHAR(4)   NOT NULL,   -- 'buy' | 'sell'
    price           FLOAT8       NOT NULL,   -- Trade price (implied probability)
    size_usd        FLOAT8       NOT NULL,   -- USD notional
    tx_hash         VARCHAR(128),            -- Polygon tx hash (Polymarket only)
    raw_json        JSONB,                   -- Original API response (for reparse)

    PRIMARY KEY (trade_id, ts_utc),
    CONSTRAINT chk_price_range CHECK (price BETWEEN 0.0001 AND 0.9999),
    CONSTRAINT chk_token       CHECK (token IN ('yes', 'no')),
    CONSTRAINT chk_side        CHECK (side IN ('buy', 'sell'))
);

SELECT create_hypertable('trades', 'ts_utc', chunk_time_interval => INTERVAL '1 day');

CREATE INDEX idx_trades_market_time ON trades (market_id, ts_utc);
CREATE INDEX idx_trades_token_time  ON trades (market_id, token, ts_utc);
```

---

## 4. `oracle_bounds` Table

Output of P4 oracle computation. One row per (slot_id × alpha × tau_label). Written by `oracle/bounds.py`.

```sql
CREATE TABLE oracle_bounds (
    slot_id       UUID        NOT NULL,
    t0_utc        TIMESTAMPTZ NOT NULL,   -- Denormalised for time-range queries
    class_code    CHAR(2)     NOT NULL,
    alpha         FLOAT4      NOT NULL,   -- α value: 0.0, 0.1, 0.25, 0.5, 0.75, 0.9, 1.0
    tau_label     VARCHAR(6)  NOT NULL,   -- 'gross' | 'uk' | 'it' | 'us'
    tau_value     FLOAT4      NOT NULL,   -- 0.0 | 0.20 | 0.26 | 0.37

    -- Oracle returns (net of fee, net of tax)
    r_l1          FLOAT8,                 -- Layer-1 oracle: outcome only, full front-load (α=1)
    r_l2          FLOAT8,                 -- Layer-2 oracle: outcome + optimal timing (α=0)
    r_parametric  FLOAT8,                 -- Parametric oracle at this α
    delta_r_timing FLOAT8,               -- ΔR_timing = R_L2 - R_L1 (constant across α for fixed slot)

    -- Crowd reference
    r_crowd       FLOAT8,                 -- E[R_crowd] = expected return betting proportional to q0
    ier           FLOAT8,                 -- IER = r_crowd / r_l2

    -- Break-even (pre-computed for this α × τ)
    p_star        FLOAT8,                 -- p*(α, f, τ) = 1 / [(α/q0 + (1-α)/q*)(1-f)(1-τ)]

    computed_at   TIMESTAMPTZ NOT NULL DEFAULT NOW(),

    PRIMARY KEY (slot_id, alpha, tau_label),
    CONSTRAINT chk_alpha_range CHECK (alpha BETWEEN 0.0 AND 1.0),
    CONSTRAINT chk_ier_range   CHECK (ier IS NULL OR (ier >= 0 AND ier <= 2.0)),
    CONSTRAINT chk_tau_label   CHECK (tau_label IN ('gross', 'uk', 'it', 'us')),
    FOREIGN KEY (slot_id) REFERENCES slot_master(slot_id) ON DELETE CASCADE
);

CREATE INDEX idx_oracle_bounds_class_time  ON oracle_bounds (class_code, t0_utc DESC);
CREATE INDEX idx_oracle_bounds_tau_alpha   ON oracle_bounds (tau_label, alpha);
```

---

## 5. `reference_prices` Table

BTC/ETH 1-second OHLCV aligned to slot boundaries. Written by P2.

```sql
CREATE TABLE reference_prices (
    slot_id         UUID        NOT NULL,
    t0_utc          TIMESTAMPTZ NOT NULL,
    asset           VARCHAR(10) NOT NULL DEFAULT 'BTC',   -- 'BTC' | 'ETH'
    price_open      FLOAT8      NOT NULL,                 -- Spot price at t0
    price_close     FLOAT8      NOT NULL,                 -- Spot price at t_close
    return_pct      FLOAT4      NOT NULL,                 -- (close/open - 1) * 100
    price_high      FLOAT8,
    price_low       FLOAT8,
    volume_base     FLOAT8,                               -- Exchange base asset volume
    source          VARCHAR(20) NOT NULL DEFAULT 'binance',
    interpolated    BOOLEAN     NOT NULL DEFAULT FALSE,   -- TRUE if 1m data was interpolated

    PRIMARY KEY (slot_id, asset),
    FOREIGN KEY (slot_id) REFERENCES slot_master(slot_id) ON DELETE CASCADE
);
```

---

## 6. `markets` Table

Market registry. Seeded from `config/markets.yaml`. Updated by P1 when new markets are discovered.

```sql
CREATE TABLE markets (
    market_id           VARCHAR(64)  PRIMARY KEY,
    platform            VARCHAR(20)  NOT NULL,
    class_code          CHAR(2)      NOT NULL,
    question_text       TEXT,                            -- Human-readable market question
    resolution_criteria TEXT,                            -- How market resolves
    active_from         DATE,
    active_to           DATE,
    condition_id        VARCHAR(128),                    -- Polymarket condition ID (hex)
    uma_contract_addr   VARCHAR(42),                     -- Polygon UMA oracle contract
    metadata_json       JSONB,                           -- Platform-specific metadata
    created_at          TIMESTAMPTZ  NOT NULL DEFAULT NOW(),
    updated_at          TIMESTAMPTZ  NOT NULL DEFAULT NOW()
);

CREATE INDEX idx_markets_platform_class ON markets (platform, class_code);
CREATE INDEX idx_markets_active         ON markets (active_from, active_to);
```

---

## 7. `resolutions` Table

Resolution records. Written by P1. Cross-checked against BTC spot by P3.

```sql
CREATE TABLE resolutions (
    market_id           VARCHAR(64)  PRIMARY KEY,
    platform            VARCHAR(20)  NOT NULL,
    resolved_at         TIMESTAMPTZ  NOT NULL,
    outcome_yes         BOOLEAN      NOT NULL,
    resolution_source   VARCHAR(50)  NOT NULL,   -- 'uma_oracle' | 'platform_api' | 'manual'
    disputed            BOOLEAN      NOT NULL DEFAULT FALSE,
    dispute_resolved_at TIMESTAMPTZ,
    tx_hash             VARCHAR(128),            -- On-chain resolution tx
    created_at          TIMESTAMPTZ  NOT NULL DEFAULT NOW(),

    FOREIGN KEY (market_id) REFERENCES markets(market_id)
);
```

---

## 8. `break_even_surface` Table

Weekly break-even p* computation. Written by P5 (`oracle/breakeven.py`).

```sql
CREATE TABLE break_even_surface (
    computed_date   DATE        NOT NULL,          -- Date this row was computed
    class_code      CHAR(2)     NOT NULL,
    platform        VARCHAR(20) NOT NULL,
    alpha           FLOAT4      NOT NULL,
    tau_label       VARCHAR(6)  NOT NULL,
    tau_value       FLOAT4      NOT NULL,
    fee_rate        FLOAT4      NOT NULL,

    -- Break-even values (computed over trailing window)
    p_star_mean     FLOAT8      NOT NULL,          -- Mean p* over trailing N slots
    p_star_median   FLOAT8,
    p_star_p5       FLOAT8,                        -- 5th percentile (best-case market)
    p_star_p95      FLOAT8,                        -- 95th percentile (worst-case market)
    p_star_ci_lo    FLOAT8,                        -- Bootstrap 95% CI lower
    p_star_ci_hi    FLOAT8,                        -- Bootstrap 95% CI upper

    -- Metadata
    n_slots         INTEGER     NOT NULL,          -- Number of slots in trailing window
    window_days     INTEGER     NOT NULL DEFAULT 7,
    computed_at     TIMESTAMPTZ NOT NULL DEFAULT NOW(),

    PRIMARY KEY (computed_date, class_code, platform, alpha, tau_label)
);
```

---

## 9. `stats_results` Table

Rolling statistical analysis output. Written by P7 (`stats/regression.py`).

```sql
CREATE TABLE stats_results (
    computed_date   DATE        NOT NULL,
    class_code      CHAR(2)     NOT NULL,
    stat_type       VARCHAR(50) NOT NULL,   -- 'ier_ols' | 'ier_autocorr' | 'ier_event' | ...
    tau_label       VARCHAR(6)  NOT NULL,
    window_days     INTEGER     NOT NULL,

    -- OLS regression (stat_type = 'ier_ols')
    coef_log_volume   FLOAT8,              -- β for log(V)
    coef_sigma_q      FLOAT8,             -- β for σ_q
    coef_q0_entropy   FLOAT8,             -- β for q0·(1-q0) entropy
    r_squared         FLOAT4,
    n_obs             INTEGER,

    -- Summary stats (stat_type = 'ier_summary')
    ier_mean          FLOAT8,
    ier_median        FLOAT8,
    ier_std           FLOAT8,
    ier_p5            FLOAT8,
    ier_p95           FLOAT8,

    -- Event detection (stat_type = 'ier_event')
    event_ts          TIMESTAMPTZ,
    ier_zscore        FLOAT4,

    result_json       JSONB,              -- Full regression output for LaTeX generation
    computed_at       TIMESTAMPTZ NOT NULL DEFAULT NOW(),

    PRIMARY KEY (computed_date, class_code, stat_type, tau_label, window_days)
);
```

---

## 10. `mc_run_registry` Table

Monte Carlo run metadata for MLflow integration. Written by P6.

```sql
CREATE TABLE mc_run_registry (
    run_id          UUID        PRIMARY KEY DEFAULT gen_random_uuid(),
    mlflow_run_id   VARCHAR(64),                    -- MLflow run ID for cross-reference
    class_code      CHAR(2)     NOT NULL,
    seed            INTEGER     NOT NULL,
    n_runs          INTEGER     NOT NULL,
    n_slots         INTEGER     NOT NULL,
    p_grid          FLOAT4[]    NOT NULL,            -- Array of p values used
    alpha_grid      FLOAT4[]    NOT NULL,            -- Array of α values used
    tau_label       VARCHAR(6)  NOT NULL,
    output_path     TEXT        NOT NULL,            -- Path to HDF5 output file
    runtime_seconds FLOAT4,
    git_commit_hash VARCHAR(40),
    started_at      TIMESTAMPTZ NOT NULL DEFAULT NOW(),
    completed_at    TIMESTAMPTZ
);
```

---

## 11. `fee_schedules` Table

Platform fee configurations. Seeded from `config/fees.yaml`.

```sql
CREATE TABLE fee_schedules (
    platform        VARCHAR(20)  NOT NULL,
    class_code      CHAR(2),                -- NULL = applies to all classes on platform
    fee_type        VARCHAR(20)  NOT NULL,   -- 'winnings' | 'maker' | 'taker' | 'commission'
    fee_rate        FLOAT4       NOT NULL,
    effective_from  DATE         NOT NULL,
    effective_to    DATE,                    -- NULL = currently active
    notes           TEXT,

    PRIMARY KEY (platform, COALESCE(class_code, ''), fee_type, effective_from)
);
```

---

## 12. Query Patterns (Reference for `db/queries.py`)

All queries in `db/queries.py` must be typed. Key patterns:

```python
# Get all clean C1 slots in a date range
def get_clean_slots(
    class_code: str,
    start: date,
    end: date,
    min_volume_usd: float = 0.0
) -> pl.LazyFrame:
    ...  # SELECT from slot_master WHERE class_code=? AND t0_utc BETWEEN ? AND ?
         #   AND data_quality_flag = 0 AND volume_usd >= ?

# Get oracle bounds for IER time-series
def get_ier_series(
    class_code: str,
    tau_label: str,
    alpha: float,
    start: date,
    end: date
) -> pl.LazyFrame:
    ...  # SELECT slot_master.t0_utc, oracle_bounds.ier, slot_master.volume_usd
         # FROM oracle_bounds JOIN slot_master USING (slot_id)
         # WHERE class_code=? AND tau_label=? AND alpha=? AND t0_utc BETWEEN ? AND ?

# Upsert slot_master row (idempotent)
def upsert_slot(slot: dict) -> None:
    ...  # INSERT INTO slot_master (...) VALUES (...) ON CONFLICT (slot_id, t0_utc) DO UPDATE SET ...
```

---

## 13. Alembic Migration Convention

- Migration scripts live in `db/migrations/versions/`
- Naming: `{revision}_{short_description}.py`
- Always include both `upgrade()` and `downgrade()` functions
- Never modify an existing migration — always create a new one
- Run with: `make schema` (which calls `alembic upgrade head`)

Migration 001 applies the full `schema.sql` DDL. All subsequent migrations are incremental ALTER TABLE / CREATE INDEX statements.