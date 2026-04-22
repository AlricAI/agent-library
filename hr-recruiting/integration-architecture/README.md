# Integration Architecture

> Date: 2026-03-10

Status: Working integration spec

## Summary

Blueprint is a three-repo system with one primary lifecycle:

1. `Blueprint-WebApp` cr

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Blueprint Integration Architecture

Date: 2026-03-10

Status: Working integration spec

## Summary

Blueprint is a three-repo system with one primary lifecycle:

1. `Blueprint-WebApp` creates and routes a scoped site request.
2. `BlueprintCapture` collects the evidence package for that request.
3. `BlueprintCapturePipeline` turns the evidence into a qualification record and handoff.
4. `Blueprint-WebApp` ingests the resulting artifacts, updates request state, and promotes qualified records into exchange and later paid lanes.

The key product rule is:

- qualification is the default product
- exchange, preview simulation, evaluation packages, scenario generation, and managed tuning are follow-on lanes
- derived assets must be stored separately from qualification truth

## Repo Responsibilities

### Blueprint-WebApp

Primary role:

- intake
- routing
- admin review
- qualified opportunity exchange
- later evaluation / tuning packaging
- monetization

Relevant models already in the repo:

- `requestId`
- `site_submission_id`
- `qualification_state`
- `opportunity_state`
- `requestedLanes`

Canonical source:

- `server/types/inbound-request.ts`

### BlueprintCapture

Primary role:

- create the evidence package for a scoped request

Minimum export bundle:

```text
raw/
  manifest.json
  intake_packet.json
  capture_context.json
  capture_upload_complete.json
  motion.jsonl
  walkthrough.mov
  optional object_index.json
  optional arkit/...
```

### BlueprintCapturePipeline

Primary role:

- convert the evidence package into:
  - qualification artifacts
  - readiness decision
  - opportunity handoff
  - human actions required
  - optional preview/evaluation artifacts

## Canonical Identity Mapping

The system needs one stable business identity and one stable capture identity.

### Business / workflow identity

- `site_submission_id`
- owner: `Blueprint-WebApp`
- lifecycle: one site/task/workflow request

Recommendation:

- use `site_submission_id` as the canonical cros

*[truncated — see source for full prompt]*