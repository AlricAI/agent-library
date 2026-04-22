# TANDEM SDK VISION

> This document has two explicit layers:

- **Layer A: Vision + Decisions** (product-readable).
- **Layer B: Runtime Contract (Normative)** (implementat

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# TANDEM SDK Vision

This document has two explicit layers:

- **Layer A: Vision + Decisions** (product-readable).
- **Layer B: Runtime Contract (Normative)** (implementation-ready).

Current runtime reality: Tandem is HTTP + SSE today (engine server endpoints + event stream).  
Stdio JSON-RPC is a later roadmap item, not a current contract.

## Layer A: Vision + Decisions

## Summary

Audience: **external builders** integrating local-first AI workflows into desktop apps, CLIs, IDE extensions, and automation pipelines.

Tandem runtime positioning: **Session-linear execution** on a **Linearizable session runtime**.

Locked decisions:

- `POST /session/{id}/message` is append-only.
- Run lock applies only to `prompt_*` execution endpoints.
- `runID` is server-issued and canonical.
- `GET /session/{id}/run` is required.
- `?return=run` escape hatch is required.
- Stale-run reaping is required.
- `prompt_sync` supports `Accept: text/event-stream`.
- `409` conflict payload uses nested `activeRun` (not flattened).

## Message vs Execution Split

- `POST /session/{id}/message`:
  - append-only
  - always allowed
  - persists messages only
- `POST /session/{id}/prompt_async`:
  - execution start
  - lock-gated
- `POST /session/{id}/prompt_sync`:
  - execution start
  - lock-gated

Desktop/Tauri intended flow:

- `/message` then `/prompt_async`
- Not "run via `/message`"

## Concurrency Model: Many Sessions = Many Agents

- A single session is intentionally linearizable and represents one active-run boundary.
- Parallel prompts inside one session are explicitly out of contract.
- Parallelism is achieved through multiple sessions (often child sessions) and aggregation.

## Migration Plan

Desktop/Tauri:

- Remove run-via-`/message` assumptions.
- Use `runID` from `?return=run` response or `GET /session/{id}/run`.
- After a reconnect, the preferred recovery primitive is `GET /session/{id}/run`, then attach via `attachEventStream` when active.
- On `409`, use `retryAfterMs` and

*[truncated — see source for full prompt]*