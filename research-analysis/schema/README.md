# SCHEMA

> This file is the **authoritative specification** for all database tables.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
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
    t0_utc               TIMESTAMPTZ NOT N

*[truncated — see source for full prompt]*