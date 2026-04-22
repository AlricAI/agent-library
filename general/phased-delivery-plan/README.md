# Phased Delivery Plan

> Status: revised plan.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Phased Delivery Plan

Status: revised plan. The architecture and public API are not marked fixed in Phase 0 anymore.

## Summary

The work is split into two tracks:

- platform track: the reusable runtime and its contracts
- product track: the LTX-first path that proves the platform under a hard workload

The stable-freeze checkpoint happens only after the platform survives more than one family and more than one task shape.

## Phase A: Platform Skeleton And Risk Closure

Goal: build the minimum platform backbone without freezing the API too early.

### Deliverables

- provider abstraction and provenance manifests
- portability classes for source refs, portable artifacts, and machine-local build cache
- control-plane daemon scaffold
- worker-process scaffold
- capability schema `v0`
- handle-based import/export model
- security baseline: UDS default, HTTP opt-in, mandatory auth rules
- operations baseline: runtime home, logs, quotas, launch strategy

### Exit criteria

- ADRs `0001` through `0005` are in place
- one provider can resolve and inspect without downloading everything blindly
- one worker can execute through the new control-plane path
- no document still claims the API is fixed

## Phase B: LTX Fast Proof Path

Goal: prove the platform on `LTX-2.3 Fast` without pretending the result generalizes automatically.

### Deliverables

- Hugging Face source resolution for LTX
- portable artifact conversion for LTX fast-path assets
- local Gemma text encoding path
- `video.generate` and `video.condition.image` job support
- truthful LTX capability reporting
- runtime-managed output artifacts

### Exit criteria

- cold pull, convert, load, and warm run metrics exist
- constraints such as resolution and frame-count rules are enforced by the platform, not only by an adapter README
- the scheduler records stage timings and memory telemetry
- LTX desktop can call the runtime in a basic thin-client mode

## Phase C: Cross-Family Platform Validation

Goal: pressure-tes

*[truncated — see source for full prompt]*