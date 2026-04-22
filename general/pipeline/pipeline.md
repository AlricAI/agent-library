---
name: PIPELINE
description: The pipeline is implemented as an **Apache Airflow DAG** (`pipeline/dags/dag_btc_pilot.
model: claude-sonnet-4-5
---
# PIPELINE.md — Pipeline Stages Reference

The pipeline is implemented as an **Apache Airflow DAG** (`pipeline/dags/dag_btc_pilot.py`) with 10 stages (P0–P9). This document specifies each stage: its trigger, inputs, outputs, implementation module, and exact exit criteria.

---

## DAG Overview

```
                       ┌─ P5 Break-Even (weekly) ─┐
P0 → P1 → P2 → P3 → P4─┤                          ├─ P9 Paper Output (weekly)
                       └─ P6 Monte Carlo (weekly)  ─┘
                             │
                             P7 Stats (daily)
                             │
                             P8 Dashboard (after P4)
```

- **Daily schedule:** P0 → P1 → P2 → P3 → P4 → P7 → P8
- **Weekly schedule:** P0 → P1 → P2 → P3 → P4 → P5 → P6 → P7 → P8 → P9
- All stages are idempotent. Failed stages can be re-run without side effects.

---

## P0 — Config & Quality Gate

**File:** `pipeline/stages/p0_config.py`
**Trigger:** Start of every DAG run (daily and weekly)
**Runtime:** < 30 seconds

### Inputs
- `config/markets.yaml` — market IDs, class codes, active date ranges
- `config/fees.yaml` — platform fee schedules
- `config/tax.yaml` — tax rates per jurisdiction
- Environment variables (API keys, DB URL)

### Processing
1. Load and validate all YAML config files (schema validation with `pydantic`)
2. Verify all required environment variables are set
3. Run Great Expectations suite on `slot_master` (prior runs' data quality)
4. Check DB connectivity (TimescaleDB + Redis)
5. Verify Polymarket API key is valid (lightweight health-check request)
6. Update `fee_schedules` table from `config/fees.yaml` if changed

### Outputs
- Validated `Config` object (passed to downstream stages via Airflow XCom)
- Great Expectations HTML report written to `data/quality_reports/{date}.html`
- Updated `fee_schedules` table rows if fees have changed

### Exit Criteria
- All config validates without errors
- GE suite passes (zero critical failures)
- DB connection successful

### Failure Behaviour
- Fail entire DAG. No downstream stages run with invalid config or bad data.

---

## P1 — Polymarket CLOB Ingestion

**File:** `pipeline/stages/p1_ingest.py`
**Trigger:** After P0 success
**Runtime:** 2–10 minutes (depending on market count and backfill depth)

### Inputs
- `config/markets.yaml` — BTC 5-min market IDs for class C1
- Polymarket CLOB REST API: `https://clob.polymarket.com`
- Polygon RPC (resolution verification): `config.POLYGON_RPC_URL`
- Target date from Airflow execution date

### Processing
1. For each active C1 market ID on the target date:
   a. Fetch all CLOB fill events in `[date 00:00:00, date+1 23:59:59]` UTC
   b. Parse fills into `trades` schema (trade_id, ts_utc, token, side, price, size_usd)
   c. Fetch resolution from Polymarket REST API: `GET /markets/{condition_id}`
   d. Cross-verify resolution with Polygon UMA oracle contract (optional, flag if mismatch)
   e. Write raw API JSON to `data/raw/{date}/{market_id}_trades.json`
   f. Upsert rows to `trades` table
   g. Upsert row to `resolutions` table
2. Discover any new C1 market IDs not yet in `markets` table; add them

### Rate Limiting
- Max 10 requests/second to Polymarket CLOB API
- Implement token-bucket limiter with `asyncio.Semaphore(10)`
- Retry: max 3 attempts, exponential backoff starting at 2s, with ±20% jitter

### Outputs
- Raw trade JSON files: `data/raw/{date}/{market_id}_trades.json`
- `trades` table: N new rows (N ≈ 500–5000 per market per day)
- `resolutions` table: updated rows for resolved markets
- `markets` table: new rows for newly discovered markets

### Exit Criteria
- At least one resolved market ingested for the target date
- Zero upsert errors
- GE row-count check: trades count > 100 for any active market day

### Failure Behaviour
- On API rate-limit: backoff and retry (do not fail DAG immediately)
- On persistent API failure (3 retries exhausted): mark task FAILED, alert, do not proceed to P2
- On partial failure (some markets failed): continue, log missing market IDs, set their `data_quality_flag = 1`

---

## P2 — Reference Price Alignment

**File:** `pipeline/stages/p2_reference.py`
**Trigger:** After P1 success
**Runtime:** 1–3 minutes

### Inputs
- `resolutions` table: resolved market IDs and their t0/t_close timestamps
- Binance REST API (ccxt): BTC/USDT 1-second OHLCV

### Processing
1. Query all markets resolved on target date from `resolutions`
2. For each market, determine the slot time window `[t0_utc − 10s, t_close_utc + 10s]`
3. Fetch BTC/USDT 1s candles for the combined window
4. For each market slot:
   a. Extract price at t0_utc: `btc_price_open = candle(t0_utc).open`
   b. Extract price at t_close_utc: `btc_price_close = candle(t_close_utc).close`
   c. Compute: `btc_return_pct = (close / open − 1) × 100`
5. If 1s candles unavailable for a date (Binance historical limit): fall back to 1m candles with linear interpolation; mark `interpolated = TRUE`
6. Upsert to `reference_prices` table

### Outputs
- `reference_prices` rows: one per resolved market slot

### Exit Criteria
- Zero NULL values in `btc_price_open` or `btc_price_close` for C1 markets
- `btc_return_pct` ≠ 0 for at least 80% of slots (guard against stale data)

---

## P3 — Slot Record Construction

**File:** `pipeline/stages/p3_slots.py`
**Trigger:** After P1 + P2 success
**Runtime:** 1–5 minutes (depending on slot count)
**Critical stage — most complex logic**

### Inputs
- `trades` table (current date's tick data)
- `resolutions` table (outcomes + timestamps)
- `reference_prices` table (BTC spot alignment)
- `markets` table (market metadata, fee rates)

### Processing

For each resolved market on target date:

**Step 1: Slot boundaries**
```
t0_utc    = first trade timestamp in market (or market open time from API)
t_close_utc = resolution timestamp from resolutions table
T_seconds = (t_close_utc − t0_utc).total_seconds()
```

Sanity check: 240 ≤ T_seconds ≤ 360 for C1. If outside range, set `quality_flag = 1`.

**Step 2: q₀ (opening price)**
```
winning_token = 'yes' if outcome_yes else 'no'
first_trades = trades WHERE market_id=X AND ts_utc BETWEEN t0 AND t0+30s
q0 = first_trades WHERE token=winning_token, first row's price
```
If no trade in first 30s: use first trade anywhere in slot. If no trades at all: `quality_flag = 3` (exclude).

**Step 3: q* (timing oracle entry)**
```
winning_trades = trades WHERE market_id=X AND token=winning_token
                           AND ts_utc BETWEEN t0 AND t_close
q_star_winner = MIN(winning_trades.price)
q_star_ts     = timestamp of that minimum trade
q_star_alpha  = (q_star_ts - t0_utc).total_seconds() / T_seconds
```
Guard: `q_star_winner = max(q_star_winner, 0.001)`
If `q_star_winner < 0.01`: `quality_flag = max(quality_flag, 1)`
If `q_star_winner > q0_yes + 0.001`: this indicates data error; `quality_flag = 2`

**Step 4: Volume and liquidity**
```
volume_usd        = SUM(all trades.size_usd) during slot
volume_winner_usd = SUM(winning_trades.size_usd) during slot
n_trades          = COUNT(all trades) during slot
sigma_q_winner    = STDDEV(winning_trades.price) during slot
price_range_winner = MAX − MIN of winning_trades.price
```
If `n_trades < 5`: `quality_flag = max(quality_flag, 1)`

**Step 5: BTC return consistency check**
```
if btc_return_pct > 0.001 and outcome_yes == False:
    quality_flag = 2  # BTC went up but market resolved NO — dispute
if btc_return_pct < -0.001 and outcome_yes == True:
    quality_flag = 2  # BTC went down but market resolved YES — dispute
```
Note: Use ±0.1% threshold to avoid flagging near-zero moves.

**Step 6: Compute slot_id**
```python
slot_id = sha256(f"polymarket:{market_id}:{t0_utc.isoformat()}").hexdigest()[:32] as UUID
```

**Step 7: Upsert to slot_master**

### Outputs
- `slot_master` rows: one per resolved market on target date
- All 26 columns populated per schema specification

### Exit Criteria
- Zero `data_quality_flag = 3` rows produced (no total failures)
- `quality_flag = 0` rows have zero NULLs in: q0_yes, q_star_winner, volume_usd, outcome_yes, btc_price_open
- BTC return sign matches outcome for all `quality_flag = 0` rows
- `q_star_winner ≤ q0_yes + 0.001` for all rows

---

## P4 — Oracle Bound Computation

**File:** `pipeline/stages/p4_oracle.py` → delegates to `oracle/bounds.py`
**Trigger:** After P3 success
**Runtime:** < 10 seconds (for single-day batch)

### Inputs
- `slot_master` WHERE `t0_utc::date = target_date` AND `data_quality_flag ≤ 1`
- `config.TAX_GRID`, `config.ALPHA_GRID`

### Processing
1. Load slots as Polars LazyFrame
2. Call `oracle.bounds.compute_oracle_bounds(slots, fee)` → LazyFrame
3. The bounds module expands each slot row into N_alpha × N_tau rows
4. For each (slot × α × τ):
   - Compute R_L1, R_L2, R_parametric, ΔR_timing
   - Compute E[R_crowd] and IER
   - Compute p* (break-even)
5. Collect and upsert to `oracle_bounds` table
6. Write IER time-series to Redis cache (key: `ier:{class_code}:{tau_label}:{alpha}`)

### Outputs
- `oracle_bounds` table: N_slots × 7 (alpha values) × 4 (tau values) = 28N rows per day
- Redis cache updated (TTL: 25 hours)

### Exit Criteria
- Zero division-by-zero errors
- All IER values: `0 ≤ IER ≤ 2.0` (IER > 1 is allowed but rare)
- `p_star ∈ [0.5, 1.0]` for all rows (or NULL for infeasible markets)
- Oracle formula unit tests (in `tests/test_oracle.py`) referenced — if they fail CI, this stage fails

---

## P5 — Break-Even Surface (Weekly)

**File:** `pipeline/stages/p5_breakeven.py` → delegates to `oracle/breakeven.py`
**Trigger:** Weekly (Sundays) after P4
**Runtime:** 2–5 minutes

### Inputs
- `oracle_bounds` table: last 7 days of data (rolling window)
- `config.TAX_GRID`, `config.ALPHA_GRID`, `config.FEE_GRID`

### Processing
1. For each (class_code × platform × α × τ × fee):
   - Compute mean, median, p5, p95 of `p_star` over trailing 7 days
   - Bootstrap 95% CI (1000 bootstrap resamples of p_star distribution)
2. Upsert to `break_even_surface` table with `computed_date = today`

### Outputs
- `break_even_surface` table rows
- LaTeX stub: `paper/tables/break_even_{class_code}_w{week}.tex`

### Exit Criteria
- `p_star_mean ∈ [0.5, 1.0]` for all rows
- `p_star_ci_lo ≤ p_star_mean ≤ p_star_ci_hi` for all rows
- LaTeX stub generated and non-empty

---

## P6 — Monte Carlo Simulation (Weekly)

**File:** `pipeline/stages/p6_montecarlo.py` → delegates to `montecarlo/spectrum.py`
**Trigger:** Weekly (Sundays) after P4
**Runtime:** 30–60 minutes (16-core CPU, 10k runs, ~50k slots)

### Inputs
- `oracle_bounds` table: ALL available data (not just last 7 days)
- `config.P_GRID`, `config.ALPHA_GRID`
- `SEED` parameter (from Airflow variable or `make mc SEED=42`)

### Processing
1. Load full oracle_bounds for C1 class as NumPy arrays:
   - `r_correct[N_slots, N_alpha]` — per-slot, per-alpha net returns when correct
   - `r_wrong[N_slots]` — per-slot net returns when wrong (= -1.0 for Phase 0)
2. Call `montecarlo.spectrum.simulate_spectrum(r_correct, r_wrong, P_GRID, N_RUNS, SEED)`
3. Post-process wealth paths tensor → summary statistics
4. Write to HDF5: `data/mc_results/{run_id}.h5`
5. Write summary CSV: `data/mc_results/{run_id}_summary.csv`
6. Log run to MLflow and `mc_run_registry` table

### Outputs
- HDF5 file with full wealth paths (shape: N_p × N_alpha × N_runs × N_slots)
- Summary CSV: mean_final_wealth, pct_5, pct_95, ruin_probability per (p, α)
- MLflow run logged
- LaTeX stub: `paper/tables/mc_summary_{class_code}.tex`

### Exit Criteria
- Run completes without memory error
- Monotonicity checks:
  - For fixed α: `mean_final_wealth(p=1.0) > mean_final_wealth(p=0.9) > ... > mean_final_wealth(p=0.5)`
  - For p=0.5: `mean_final_wealth < 1.0` (random agent loses)
  - For p=1.0: `mean_final_wealth > 1.0` (oracle wins)
- `ruin_probability(p=0.5) > ruin_probability(p=0.75) > ruin_probability(p=1.0)`

---

## P7 — Statistical Analysis

**File:** `pipeline/stages/p7_stats.py` → delegates to `stats/regression.py`
**Trigger:** Daily, after P4
**Runtime:** < 2 minutes

### Inputs
- `oracle_bounds` table: rolling 30-day window, tau_label='it', alpha=1.0
- `slot_master` table: matching slots (for volume and sigma_q covariates)

### Processing
1. OLS regression: `IER ~ log(V) + sigma_q + q0_entropy + day_of_week_dummies`
   - `q0_entropy = q0_yes × log(q0_yes) + q0_no × log(q0_no)` (Shannon entropy)
   - Clustered standard errors by week
2. Rolling 7-day IER mean and std
3. IER z-score detection: flag slots where `|IER − rolling_mean| > 2 × rolling_std`
4. Upsert results to `stats_results` table
5. Write regression LaTeX stub: `paper/tables/ier_regression_c1.tex`

### Outputs
- `stats_results` rows (stat_type: 'ier_ols', 'ier_summary', 'ier_event')
- LaTeX regression table stub

### Exit Criteria
- Regression converges
- R² reported (no threshold — just must be present)
- LaTeX stub written

---

## P8 — Dashboard Refresh

**File:** `pipeline/stages/p8_dashboard.py`
**Trigger:** Daily, after P4
**Runtime:** < 30 seconds (just updates Redis / Dash data store)

### Inputs
- Redis oracle cache (written by P4)
- `stats_results` table (rolling IER summary from P7)
- `break_even_surface` table (latest values from P5)
- `mc_run_registry` table (latest MC summary path)

### Processing
1. Push updated data to Dash DataStore components via Redis pub/sub
2. Update plain-language break-even sentence: `"To break even in BTC 5-min markets today (Italian tax), you need to be right on more than {p_star_pct:.1f}% of your bets."`
3. Trigger dashboard hot-reload (Dash polling interval catches this automatically)

### Exit Criteria
- Dashboard at `:8050` shows data from target date's run within 60 seconds

---

## P9 — Paper Output Generation (Weekly)

**File:** `pipeline/stages/p9_paper.py` → delegates to `viz/figures/generate.py`
**Trigger:** Weekly (Sundays) after P5 + P6 + P7
**Runtime:** 5–10 minutes

### Inputs
- `oracle_bounds` table (full history)
- `break_even_surface` table (latest weekly computation)
- MC summary CSV (latest run from `mc_run_registry`)
- `stats_results` table (latest regression)

### Outputs (all committed to git)
- `paper/tables/oracle_bounds_summary_c1.tex` — oracle bounds descriptive stats
- `paper/tables/break_even_btc_c1.tex` — break-even surface table
- `paper/tables/mc_summary_c1.tex` — Monte Carlo quantile table
- `paper/tables/ier_regression_c1.tex` — OLS regression table
- `paper/figures/ier_timeseries_c1.pdf` — IER time-series plot
- `paper/figures/oracle_surface_c1.pdf` — (p, α) expected return heatmap
- `paper/figures/breakeven_surface_c1.pdf` — break-even surface 3D plot
- `paper/figures/fee_drag_curve_c1.pdf` — net return vs. trade frequency

### Exit Criteria
- All 4 LaTeX stubs written and non-empty
- All 4 figures written as valid PDFs
- Each figure's filename matches exactly (paper source imports by exact name)

---

## Airflow DAG Configuration Notes

```python
# pipeline/dags/dag_btc_pilot.py — key settings
default_args = {
    "owner": "oracle-gap",
    "retries": 3,
    "retry_delay": timedelta(minutes=5),
    "retry_exponential_backoff": True,
    "on_failure_callback": alert_on_failure,  # sends email via Airflow connection
}

dag = DAG(
    "btc_pilot_daily",
    schedule_interval="5 0 * * *",  # 00:05 UTC daily
    start_date=datetime(2024, 1, 1),
    catchup=True,   # Enable backfill
    max_active_runs=3,
    tags=["oracle-gap", "phase-0", "c1"],
)
```

The weekly trigger uses a separate DAG (`btc_pilot_weekly`) with `schedule_interval="5 0 * * 0"` (Sundays) that depends on `btc_pilot_daily` having succeeded for all 7 days.