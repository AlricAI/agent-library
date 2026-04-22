# Benchmark Matrix

> Status: required before the architecture or public API can be called stable.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Benchmark Matrix

Status: required before the architecture or public API can be called stable.

## Purpose

This matrix replaces demo-level acceptance criteria with freeze-grade evidence.

The runtime is not considered validated because it can “run once.” It is validated only when it survives the matrix below with recorded timings, memory, and failure behavior.

## Required Axes

| Axis | Minimum coverage |
| --- | --- |
| Families | `LTX-2.3 Fast` T2V, `LTX-2.3 Fast` I2V, one image diffusion family, one non-generation family, one TTS or audio family, one VLM, and one text family or an explicit freeze-blocking exclusion |
| Hardware | at least one `32 GB`, one `64 GB`, and one `128 GB` Apple Silicon tier; include one older Max-class machine and one newer Max-class machine if available |
| Run state | cold inspect, cold fetch, cold convert, cold load, warm load, warm run, model switch |
| Concurrency | isolated heavy job, heavy plus light, multiple light jobs, cancellation under load |
| Output path | model-only time, decode time, encode or mux time, export time |
| Precision and profile | baseline float path, q8, lower-bit profiles where meaningful, selective quantization where applicable |
| Shapes | common bucketed shapes and deliberately off-bucket shapes |

## Required Workload Basket

| Family | Why it is required |
| --- | --- |
| `LTX-2.3 Fast` T2V | hardest current product pressure: staged video generation, strict constraints, big memory, output muxing |
| `LTX-2.3 Fast` I2V | forces conditioning and artifact handle flow |
| Image diffusion | validates non-LTX media generation without LTX-specific assumptions |
| Whisper or equivalent | validates non-generation pipeline stages and different scheduler behavior |
| TTS or audio family | validates audio outputs, vocoder or chunking pressure |
| VLM | validates mixed-modality processors and interactive generation patterns |
| Text family | validates whether the platform can honestly support text-serving pressu

*[truncated — see source for full prompt]*