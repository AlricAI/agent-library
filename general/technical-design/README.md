# Technical Design

> Status: provisional architecture.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# MLXR Technical Design

Status: provisional architecture. This is the working design to implement against now, but it is not the final frozen public contract. API freeze is gated by the benchmark matrix and cross-family validation.

## Summary

The runtime is split into a platform track and a product track.

- The platform track defines the source model, artifact model, provenance model, security posture, scheduler, worker topology, and host surfaces.
- The product track uses `LTX-2.3 Fast` to pressure-test those decisions on a hard Apple Silicon workload.

The architecture that survives review is:

- one canonical local runtime
- a native job-oriented API as the source of truth
- provider adapters and family adapters as separate seams
- a control-plane daemon plus execution workers
- portability classes separated into source references, portable artifacts, and machine-local build cache
- Python-first workers, Swift earlier at the host boundary, C++/Metal as an explicit hotspot seam

## Architecture Status

### Strong decisions

- one runtime, many surfaces
- native API first, compatibility facades second
- Python-first model-family bring-up
- thin host adapters
- LTX as the first proving workload

### Provisional decisions

- exact worker granularity
- exact capability schema version `1`
- exact handle import/export flows
- final scheduler heuristics and reservation formulas
- exact MLX extension backlog

Those decisions stay provisional until the validation plan upgrades them.

## Top-Level Architecture

```text
Hosts
  CLI / SDK / Desktop / Comfy / Embedded First-Party Apps
                  |
                  v
        Control-Plane Daemon
  - transport + auth
  - provider resolution
  - provenance + policy store
  - artifact index
  - scheduler
  - capability service
  - job store + event stream
                  |
                  +--> Family worker: LTX
                  +--> Family worker: image diffusion
                  +--> Family worker: speech or VL

*[truncated — see source for full prompt]*