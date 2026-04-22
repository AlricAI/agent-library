# V2026.319.0

> > Released: 2026-03-19

## Highlights

- **Paperclip refactor foundation** - The startup path has been decomposed into dedicated bootstrap helpers, ma

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Paperclip Refactor Foundation

> Released: 2026-03-19

## Highlights

- **Paperclip refactor foundation** - The startup path has been decomposed into dedicated bootstrap helpers, making server initialization easier to understand, test, and maintain.
- **Centralized public URL resolution** - Access and onboarding now share a single public URL resolver, reducing duplication and making onboarding behavior more consistent.
- **Heartbeat profiling and baselines** - The heartbeat runtime now has opt-in profiling plus real baselines for minimal, project-scoped, maintenance, and queue-contention scenarios.
- **Safe runtime tuning** - `tickTimers()` now filters eligible agents in SQL and only projects the fields it needs, reducing unnecessary work without changing scheduler semantics.
- **OpenClaw orchestration skill** - A dedicated skill and supporting artifacts were added to coordinate future multi-agent refactors on this fork.

## Improvements

- **Bootstrap modularization** - `server/src/index.ts` now delegates deployment validation, authenticated-mode wiring, schedulers, and listener startup to dedicated helpers.
- **Onboarding contract hardening** - Public URL resolution now prefers explicit configured bases over forwarded-header inference, with legacy behavior preserved only as a fallback.
- **Validation coverage** - New unit and orchestration tests cover deployment config, authenticated mode, public URL resolution, heartbeat schedulers, listener startup, and the startup orchestration path.
- **Release documentation** - Added English documentation for startup composition, access/onboarding behavior, heartbeat runtime behavior, testing evidence, and final release readiness.
- **Refactor governance** - Added plan, workboard, risks, decisions, status, and test matrix documents to keep the execution model auditable.

## Fixes

- **Startup coupling** - Large chunks of server startup logic were split into smaller modules to reduce the risk of regressions during future cha

*[truncated — see source for full prompt]*