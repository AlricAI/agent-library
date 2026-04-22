# Ops Agent Fix List 2026 04 01

> This fix list turns the April 1, 2026 Paperclip failure audit into four concrete workstreams.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Ops Agent Fix List

This fix list turns the April 1, 2026 Paperclip failure audit into four concrete workstreams.

## 1. Paperclip Stability / Embedded Postgres Restarts

### Goal

Stop `process_lost` heartbeat failures caused by Paperclip restarts and local DB lock/startup races.

### Observed Failures

- `63` failed heartbeats with `Process lost -- server may have restarted`
- `5` additional failed heartbeats with lost child PIDs
- launchd maintenance loop parsing empty JSON and probing the wrong local API port
- embedded Postgres startup errors in server stderr:
  - empty `postmaster.pid`
  - failed embedded Postgres startup on `54329`
  - null socket write crash after startup failure

### Immediate Fixes

1. Move the shared Paperclip instance off embedded Postgres.
   - Add a real `DATABASE_URL` to the Paperclip env file used by launchd.
   - Rationale: the current shared instance is no longer a good fit for embedded Postgres.
   - Control point: `/Users/nijelhunt_1/workspace/paperclip/server/src/index.ts`

2. Normalize Paperclip local API defaults across all Blueprint scripts.
   - Keep one canonical port for this shared instance.
   - Today bootstrap uses `3100`, but reconcile/verify/smoke use `3101`.
   - Control points:
     - `/Users/nijelhunt_1/workspace/Blueprint-WebApp/scripts/paperclip/bootstrap-blueprint-paperclip.sh`
     - `/Users/nijelhunt_1/workspace/Blueprint-WebApp/scripts/paperclip/reconcile-blueprint-paperclip-company.sh`
     - `/Users/nijelhunt_1/workspace/Blueprint-WebApp/scripts/paperclip/verify-blueprint-paperclip.sh`
     - `/Users/nijelhunt_1/workspace/Blueprint-WebApp/scripts/paperclip/smoke-blueprint-paperclip-automation.sh`

3. Make maintenance scripts tolerate empty or unavailable API responses.
   - Replace direct `JSON.parse(text)` on curl output with:
     - a non-empty-body check
     - a retry/backoff path
     - a clearer health-check failure message
   - Primary control point:
     - `/Users/nijelhunt_1/workspace/Blueprint-W

*[truncated — see source for full prompt]*