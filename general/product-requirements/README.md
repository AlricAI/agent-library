# Product Requirements

> Status: provisional product requirements for platform and first product track.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# MLXR Product Requirements

Status: provisional product requirements for platform and first product track. These requirements are concrete enough to guide implementation, but they do not freeze the public API or the final worker topology.

## Vision

Build the best local-first generative and multimodal runtime for Apple Silicon.

That means:

- users point the runtime at model sources they are allowed to use
- the runtime preserves provenance, access state, and policy
- the runtime fetches, validates, converts, caches, schedules, and serves those models locally
- every host surface sees one truthful capability model instead of inventing its own inference contract

The current scope is universal across host surfaces and model-family adapters for local generative and multimodal workloads. It is not yet a claim of support for every possible MLX workload class.

## Product Thesis

The product is not “an MLX port of LTX.” It is:

- a reusable Apple Silicon runtime
- with LTX as the first proving workload
- designed so additional image, video, audio, speech, VLM, and selected text families can land without rewriting host integrations

The runtime should create value in two layers:

1. As a platform: one source/provenance model, one artifact model, one scheduler, one native API, one operations model.
2. As a product: a clean local experience for difficult workloads that official upstream tools do not support well on macOS today.

## Scope We Can Defend

### Universal across

- host surfaces: CLI, local daemon, desktop adapters, Comfy adapters, embedded first-party use
- model-family architecture: video, image, audio, speech, VLM, and at least one text family as a validation pressure test
- provider architecture: the runtime models multiple providers even if v1 only implements a small subset

### Not yet universal across

- every provider in implementation
- every MLX workload class
- every public API shape
- every hardware tier

## Primary Users

### 1. Local creators

Th

*[truncated — see source for full prompt]*