---
name: ARCHITECTURE
description: ---

## 1. Design Philosophy: Build General, Deploy Specific

The system is designed so that adding a new market class (e.g., Fed rate decisions on Ka
model: claude-sonnet-4-5
---
# ARCHITECTURE.md — System Architecture Reference

---

## 1. Design Philosophy: Build General, Deploy Specific

The system is designed so that adding a new market class (e.g., Fed rate decisions on Kalshi) requires:
- One new Python file (`ingestion/kalshi.py`)
- Entries in `config/markets.yaml` and `config/fees.yaml`
- Zero changes to any other module

This is enforced by the architecture: `oracle/`, `montecarlo/`, `stats/`, and `viz/` have no knowledge of market classes or platforms. They only know the `slot_master` schema.

---

## 2. Five-Layer Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│  LAYER 1 — INGESTION                                                │
│  ingestion/polymarket.py  ·  ingestion/binance.py  ·  base.py       │
│  async httpx  ·  ccxt  ·  web3.py  ·  Polygon RPC                  │
│  → Raw tick parquet  ·  TimescaleDB: trades, reference_prices       │
└─────────────────────┬───────────────────────────────────────────────┘
                      │  tick events + resolution records
┌─────────────────────▼───────────────────────────────────────────────┐
│  LAYER 2 — ORCHESTRATION                                            │
│  Apache Airflow 2.9  ·  10-stage DAG  ·  daily + weekly schedule   │
│  LocalExecutor  ·  idempotent tasks  ·  Great Expectations gate     │
│  → Pipeline execution, scheduling, retry, alerting                  │
└─────────────────────┬───────────────────────────────────────────────┘
                      │  orchestrates ↓
┌─────────────────────▼───────────────────────────────────────────────┐
│  LAYER 3 — STORAGE                                                  │
│  TimescaleDB: trades, slot_master*, oracle_bounds, reference_prices │
│  PostgreSQL: markets, resolutions, fee_schedules, stats_results     │
│  Redis: oracle bounds cache (TTL 25h)  ·  Dashboard data store     │
│  *slot_master = central data artefact                               │
└─────────────────────┬───────────────────────────────────────────────┘
                      │  slot_master rows
┌─────────────────────▼───────────────────────────────────────────────┐
│  LAYER 4 — COMPUTE                                                  │
│  oracle/bounds.py      (Polars vectorised, < 2s / 100k slots)       │
│  oracle/breakeven.py   (SciPy brentq, weekly batch)                 │
│  montecarlo/spectrum.py (Numba @njit parallel, ~45 min / 10k runs)  │
│  stats/regression.py   (statsmodels OLS + panel FE, daily)          │
└─────────────────────┬───────────────────────────────────────────────┘
                      │  oracle bounds, IER, MC distributions
┌─────────────────────▼───────────────────────────────────────────────┐
│  LAYER 5 — OUTPUT                                                   │
│  viz/dashboard/app.py    (Plotly Dash, :8050, live-updatable)       │
│  viz/figures/generate.py (Matplotlib PDF, deterministic)            │
│  pipeline/stages/p9_paper.py  (LaTeX table stubs → paper/)         │
│  MLflow experiment registry                                         │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 3. Data Flow (Detailed)

```
Polymarket CLOB API
  │
  ├─[P1]→ trades table (TimescaleDB)
  │         │
  │         └─[P3]─────────────────────────────────────┐
  │                                                     │
Binance 1s OHLCV                                        │
  │                                                     │
  └─[P2]→ reference_prices table                       │
                      │                                 ▼
                      └──────────────────→ slot_master table
                                                        │
                                           [P4] oracle/bounds.py
                                                        │
                                           oracle_bounds table + Redis cache
                                           │                    │
                            ┌─────────────┤             [P8] Dashboard
                            │             │
                          [P5]          [P7] stats/regression.py
                   oracle/breakeven.py      │
                            │          stats_results table
                   break_even_surface       │
                            │         ─────┘
                          [P6]       [P9] paper output
                 montecarlo/spectrum.py     │
                            │          paper/tables/*.tex
                    mc_results HDF5    paper/figures/*.pdf
                            │
                    MLflow registry
```

---

## 4. Module Interfaces

### 4.1 `ingestion/base.py` — Abstract Ingestor Interface

```python
from abc import ABC, abstractmethod
from datetime import date, datetime
from dataclasses import dataclass
import polars as pl

@dataclass
class Resolution:
    market_id: str
    platform: str
    resolved_at: datetime
    outcome_yes: bool
    resolution_source: str
    disputed: bool = False
    tx_hash: str | None = None

class BaseIngestor(ABC):
    """All ingestors must implement these three methods."""

    @abstractmethod
    async def fetch_trades(self, market_id: str, date: date) -> pl.DataFrame:
        """
        Returns DataFrame with columns:
          trade_id: str, market_id: str, platform: str, ts_utc: datetime,
          token: str ('yes'|'no'), side: str ('buy'|'sell'),
          price: float, size_usd: float, tx_hash: str|None, raw_json: dict
        """

    @abstractmethod
    async def fetch_resolution(self, market_id: str) -> Resolution:
        """Returns resolution record for a market. Raises if market not yet resolved."""

    @abstractmethod
    async def get_market_ids(self, class_code: str, date: date) -> list[str]:
        """Returns all active market IDs for the given class on the given date."""
```

### 4.2 `oracle/bounds.py` — Oracle Computation Interface

```python
import polars as pl

# Module-level constants (do not change without updating tests)
ALPHA_GRID = [0.0, 0.1, 0.25, 0.5, 0.75, 0.9, 1.0]
TAX_GRID   = {"gross": 0.0, "uk": 0.20, "it": 0.26, "us": 0.37}

def r_l1(q0: float, q_star: float, f: float, tau: float, alpha: float = 1.0) -> float:
    """Layer-1 oracle return. alpha parameter ignored (always 1.0), kept for interface consistency."""

def r_l2(q0: float, q_star: float, f: float, tau: float) -> float:
    """Layer-2 (dual) oracle return. Always uses alpha=0."""

def r_parametric(alpha: float, q0: float, q_star: float, f: float, tau: float) -> float:
    """Parametric oracle return at arbitrary alpha."""

def delta_r_timing(q0: float, q_star: float, f: float, tau: float) -> float:
    """Timing premium = R_L2 - R_L1."""

def expected_return(p: float, alpha: float, q0: float, q_star: float, f: float, tau: float) -> float:
    """E[R_net](p, alpha) for a single slot."""

def ier(r_crowd: float, r_l2: float) -> float:
    """Information Efficiency Ratio. Returns NaN if r_l2 <= 0."""

def compute_oracle_bounds(slots: pl.LazyFrame, fee: float) -> pl.LazyFrame:
    """
    Main computation function. Expands each slot row into ALPHA_GRID × TAX_GRID rows.

    Input schema: slot_master columns (at minimum: q0_yes, q_star_winner, fee_rate)
    Output schema: all input columns + alpha, tau_label, tau_value,
                   r_l1, r_l2, r_parametric, delta_r_timing, r_crowd, ier, p_star
    """
```

### 4.3 `oracle/breakeven.py` — Break-Even Interface

```python
def break_even_p(
    alpha: float,
    q0: float,
    q_star: float,
    f: float,
    tau: float,
) -> float:
    """
    Compute p*(alpha, f, tau) = 1 / [(alpha/q0 + (1-alpha)/q_star) * (1-f) * (1-tau)]

    Returns p* in [0.5, 1.0]. Returns 1.0 if oracle cannot break even.
    """

def compute_breakeven_surface(
    slots: pl.LazyFrame,
    alpha_grid: list[float],
    tax_grid: dict[str, float],
    window_days: int = 7,
) -> pl.DataFrame:
    """
    Compute break-even surface over a rolling window of slots.
    Returns DataFrame with columns: alpha, tau_label, p_star_mean, p_star_median,
                                    p_star_p5, p_star_p95, p_star_ci_lo, p_star_ci_hi, n_slots
    """
```

### 4.4 `montecarlo/spectrum.py` — Monte Carlo Interface

```python
import numpy as np
import numba

# Module-level grid constants
P_GRID     = np.array([0.50, 0.55, 0.60, 0.65, 0.70, 0.75, 0.80, 0.85, 0.90, 0.95, 1.00])
ALPHA_GRID = np.array([0.00, 0.10, 0.25, 0.50, 0.75, 0.90, 1.00])
N_RUNS     = 10_000

@numba.njit(parallel=True, cache=True)
def simulate_spectrum(
    r_correct: np.ndarray,  # shape (N_slots, N_alpha) — net returns when investor correct
    r_wrong:   np.ndarray,  # shape (N_slots,) — net returns when wrong (= -1.0 - gas)
    p_grid:    np.ndarray,  # shape (N_p,)
    n_runs:    int,
    seed:      int,
) -> np.ndarray:            # shape (N_p, N_alpha, N_runs, N_slots) — cumulative wealth

def summarise_paths(
    wealth_paths: np.ndarray,
    p_grid: np.ndarray,
    alpha_grid: np.ndarray,
) -> dict:
    """
    Post-process wealth paths into summary statistics.
    Returns dict with keys: mean_final, p5_final, p95_final, ruin_prob
    Each value is shape (N_p, N_alpha).
    """
```

### 4.5 `db/queries.py` — Database Interface

```python
import polars as pl
from datetime import date
from typing import Any

# All functions accept a connection parameter (psycopg2 connection or connection pool)

def get_clean_slots(conn, class_code: str, start: date, end: date,
                    min_volume_usd: float = 0.0) -> pl.LazyFrame:
    """Returns clean (flag=0) slots as Polars LazyFrame."""

def upsert_slot(conn, slot: dict[str, Any]) -> None:
    """Upsert a single slot_master row. Idempotent on slot_id."""

def upsert_oracle_bounds(conn, bounds_df: pl.DataFrame) -> int:
    """Upsert oracle_bounds rows. Returns count of rows written."""

def get_ier_series(conn, class_code: str, tau_label: str, alpha: float,
                   start: date, end: date) -> pl.LazyFrame:
    """Returns IER time-series with volume for regression analysis."""

def get_latest_breakeven(conn, class_code: str, platform: str) -> pl.DataFrame:
    """Returns the most recent break-even surface for a class."""
```

---

## 5. Configuration Schema

### `config/markets.yaml`

```yaml
polymarket:
  class_C1:
    - market_id: "0xabcdef1234567890abcdef"
      question: "Will Bitcoin be higher 5 minutes from now?"
      active_from: "2024-01-01"
      active_to: null           # null = currently active
      condition_id: "0xabc..."  # hex condition ID for Polygon verification
      uma_contract: "0x1234..." # UMA oracle adapter address
```

### `config/fees.yaml`

```yaml
polymarket:
  default:
    fee_type: winnings          # fee applied to gross winnings
    fee_rate: 0.02              # 2%
    effective_from: "2023-01-01"
```

### `config/tax.yaml`

```yaml
jurisdictions:
  gross:
    tau: 0.00
    label: "Pre-tax"
  uk:
    tau: 0.20
    label: "UK CGT 20%"
  it:
    tau: 0.26
    label: "Italian Capital Gains 26%"
  us:
    tau: 0.37
    label: "US Short-Term ~37%"
```

---

## 6. Container Services

| Service | Image | Port | Purpose |
|---------|-------|------|---------|
| `timescaledb` | `timescale/timescaledb:2.14-pg16` | 5432 | Primary data store |
| `redis` | `redis:7.2-alpine` | 6379 | Oracle cache + Dash data store |
| `airflow` | `apache/airflow:2.9.2` | 8080 | Pipeline orchestration UI |
| `dashboard` | Custom build | 8050 | Plotly Dash live dashboard |

All services communicate over the `oracle-gap` Docker network. Services are defined in `docker-compose.yml`. Secrets are injected via `.env`.

---

## 7. Performance Targets

| Operation | Target | Notes |
|-----------|--------|-------|
| P1 ingestion (1 day, C1) | < 10 min | ~500–5000 trades |
| P3 slot construction (1 day) | < 2 min | ~300 slots |
| P4 oracle bounds (1 day, full grid) | < 10 sec | Polars lazy eval |
| P4 oracle bounds (100k slots) | < 2 sec | Benchmark target |
| P5 break-even surface (7-day) | < 5 min | SciPy brentq |
| P6 Monte Carlo (10k runs, 50k slots) | < 60 min | Numba parallel, 16-core |
| P6 Monte Carlo (with GPU) | < 5 min | CuPy optional |
| P7 statistical analysis | < 2 min | statsmodels OLS |
| Dashboard IER time-series load | < 1 sec | Redis cache hit |

---

## 8. Scalability Model

The system is designed to run on a single machine. The decision not to use distributed compute (Kubernetes, Spark, Dask) is intentional:

- **TimescaleDB** handles 100M+ tick rows with time-partitioned hypertables. Compression reduces storage by ~90%.
- **Polars** with lazy evaluation processes the oracle computation without loading full tick history into RAM.
- **Numba** with `parallel=True` automatically uses all available CPU cores.
- **Airflow with LocalExecutor** is sufficient for a single-node pipeline without the overhead of a distributed executor.

If the dataset grows beyond single-machine capacity (unlikely for Phase 0–1), the migration path is: TimescaleDB → TimescaleDB Cloud, Airflow LocalExecutor → CeleryExecutor with a worker pool, Numba → CuPy (GPU) or Dask.