# Mac App Runtime Contract

> Status: canonical host/runtime boundary for the first-party Mac app

## Summary

The Mac app is a thin native client over the same runtime contract us

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# MLXR Mac App Runtime Contract

Status: canonical host/runtime boundary for the first-party Mac app

## Summary

The Mac app is a thin native client over the same runtime contract used by the
CLI and future adapters.

The runtime owns:

- capability truth
- planning truth
- run acceptance truth

The app owns:

- presentation
- organization
- UX language

No host should invent a second workflow-validity matrix, a second model-default
system, or a family-specific inference path.

## Canonical Runtime Seams

The Mac app, CLI, and future adapters should consume the same runtime seams:

- `/v1/capabilities`
- `/v1/models`
- `/v1/models/supported`
- `/v1/workflows/plan`
- `/v1/workflows/run`
- `/v1/jobs`
- input import routes
- output export routes

`/v1/workflows/plan` is the readiness source for draft validation.

## Planning Truth

`WorkflowPlanResult.readiness` tells hosts:

- whether the draft is runnable
- what is blocking
- which references are required
- which output formats are allowed

Capability numeric constraints remain the source of:

- width truth
- height truth
- frame-count truth
- inference-step truth
- guidance-scale truth

Hosts may shape UX around those facts, but they must not redefine them.

## Host Boundary Rules

The Mac app should:

- keep its draft in app state rather than view-local temporary state
- debounce planning through `/v1/workflows/plan`
- create visible run-group activity only after the runtime accepts a run
- present runtime-backed installs, jobs, and artifacts truthfully
- keep advanced host-side helpers optional and non-authoritative

The Mac app should not:

- own scheduling
- own inference logic
- own family-specific stage sequencing
- own capability validation truth
- create app-only model-default ranking tables that drift from the runtime

## Surface Rules

### Library

- Library is asset-first, not job-first.
- Generated outputs and imported assets share one asset model.
- Focused preview opens in a large modal viewer, not a 

*[truncated — see source for full prompt]*