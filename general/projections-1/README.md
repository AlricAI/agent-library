# Projections

> How koan maintains frontend-visible state as a versioned event log with a
materialized projection, served to the browser as JSON Patch diffs over SSE.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Projections

How koan maintains frontend-visible state as a versioned event log with a
materialized projection, served to the browser as JSON Patch diffs over SSE.

> Parent doc: [architecture.md](./architecture.md)

---

## Overview

The projection system maintains:

1. An **append-only versioned event log** — every fact that occurs during a
   workflow run, in order, with a monotonically increasing version number.
2. A **materialized projection** — the complete frontend-visible state derived
   by folding the event log with a pure function.
3. A **diff engine** — `jsonpatch.make_patch` computes RFC 6902 JSON Patch
   operations between projection states, broadcast to SSE subscribers.
4. A **subscriber mechanism** — one `asyncio.Queue` per connected SSE client,
   fed from `push_event()`.

The `/events` SSE endpoint sends a full snapshot on connect or reconnect, then
streams JSON Patch operations for every subsequent state change.

**Design invariant:** The fold runs only in Python. The frontend applies
server-computed patches mechanically — it has no fold logic, no event
interpretation, and no business rules.

---

## The Event Log

All events share a common envelope. `agent_id` is set when the event originates
from a specific agent; `None` otherwise.

```python
class VersionedEvent(BaseModel):
    version: int                    # 1-based, monotonic
    event_type: str                 # one of the event types (stored as str for forward compat)
    timestamp: str                  # ISO8601 UTC
    agent_id: str | None = None     # originating agent, when known
    payload: dict                   # typed per event_type (see below)
```

The log is append-only. Events are never modified or removed. The entire log is
held in memory for the duration of a workflow run.

---

## Event Types (38 total)

### Lifecycle (10)

| Event | Payload | `agent_id` |
|-------|---------|-----------|
| `run_started` | `{profile, installations, scout_concurrency}` | `None` |
| `workfl

*[truncated — see source for full prompt]*