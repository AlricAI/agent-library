# CELERY FLOW

> This doc explains **how a Celery task flows** through the stack and **how you can see it** (logs, API, Flower, metrics).

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Celery flow – how to see it

This doc explains **how a Celery task flows** through the stack and **how you can see it** (logs, API, Flower, metrics).

---

## 1. End-to-end flow (high level)

```
  TRIGGER                    BROKER                 WORKER                    RESULT
  ───────                    ──────                  ──────                    ──────

  Option A: Celery Beat (schedule)
  ┌──────────────┐           ┌──────────────┐       ┌──────────────┐         ┌──────────────┐
  │ celery-beat  │  ──────▶  │ Redis        │  ───▶  │ celery-worker│  ───▶   │ Redis        │
  │ (scheduler)   │  publish  │ (broker)     │  consume │ (runs task)  │  store  │ (result      │
  │ every 5s etc │           │              │         │              │         │  backend)    │
  └──────────────┘           └──────────────┘       └──────────────┘         └──────────────┘
                                                                                     │
  Option B: API (on-demand)                                                           │
  ┌──────────────┐           same broker               same worker                     │
  │ FastAPI      │  .delay() ────────────────────────────────────────────────▶  task_id, result
  │ /market-data/│           or .apply_async()                                      │
  │ fetch/async  │                                                                   ▼
  └──────────────┘                                                    Poll GET /task/{id} or
                                                                       wait .get(timeout=…)
```

- **Trigger**: either **Celery Beat** (schedule in `src/core/celery_app.py`) or **API** (e.g. `POST /api/v1/market-data/fetch/async`).
- **Broker**: Redis (e.g. `CELERY_BROKER_URL=redis://redis:6379/0`). Tasks are queued here.
- **Worker**: `celery -A src.core.celery_app worker -l info -Q default,data_processing,...` consumes from Redis and runs the task code.
- **Result**: Stored in Redis (r

*[truncated — see source for full prompt]*