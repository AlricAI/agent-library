# Current Status

> Last updated: 2026-03-15

## Snapshot

`MLXR` is already a real local runtime on Apple Silicon, but it is not yet a
fully polished public product.

Wh

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# MLXR Current Status

Last updated: 2026-03-15

## Snapshot

`MLXR` is already a real local runtime on Apple Silicon, but it is not yet a
fully polished public product.

What is real today:

- one shared runtime with provider, provenance, artifact, and job models
- a real first-party CLI over the local daemon
- real LTX, Qwen-Image, FLUX.2, and Z-Image family slices
- a growing cross-family capability story
- an early buildable first-party Mac app package over the same runtime

What is not true yet:

- frozen public API
- finished desktop adapter support
- a released polished first-party Mac app
- a fully green open-source release posture

## Surface Status

| Surface | Current status | Notes |
| --- | --- | --- |
| Shared runtime | real | canonical source of truth |
| Local daemon API | real | UDS-first, handle-based |
| `mlxr` CLI | real | first-party thin client with `generate`, `serve`, `doctor`, `models`, and `feedback` |
| `ltx-desktop` adapter | planned | compatibility seam, not yet implemented |
| Comfy adapter | planned | thin runtime-backed adapter, not yet implemented |
| First-party Mac app | early implementation | buildable native Swift package over the shared runtime, now with a shared floating composer, compact project-first `Library`, square-tile project detail with modal viewer, no visible or hidden `Studio` destination, rail-based `Activity`, guided model installs, and a real dev `.app` bundle path for macOS/Peekaboo testing |
| Embedded first-party access | planned later | Swift-side host boundary work |

## Family Truth

| Family | Current promoted truth | Current supported but unpromoted truth | Still blocked or later |
| --- | --- | --- | --- |
| LTX-2.3 | distilled `video.generate`, distilled `video.condition.image`, conditioned-audio, audio-bearing outputs | `one_stage`, `two_stage`, `two_stage_hq`, retake, interpolation, broader IC-LoRA control rows | fully promoted `dev` family closure, desktop compatibility adapter |
| Z-Image | prompt-on

*[truncated — see source for full prompt]*