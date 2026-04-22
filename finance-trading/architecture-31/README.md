# ARCHITECTURE

> ---

## 1. Design Philosophy: Build General, Deploy Specific

The system is designed so that adding a new market class (e.g., Fed rate decisions on Ka

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
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
└─────────────────────┬────────────

*[truncated — see source for full prompt]*