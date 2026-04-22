# PIPELINE

> The pipeline is implemented as an **Apache Airflow DAG** (`pipeline/dags/dag_btc_pilot.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
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

##

*[truncated — see source for full prompt]*