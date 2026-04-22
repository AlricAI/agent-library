# Capability Schema

> Status: provisional schema `v0`.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Capability Schema

Status: provisional schema `v0`. This is concrete enough to drive implementation and host integration, but it should not be versioned as stable until the freeze criteria pass.

## Purpose

The capability descriptor tells hosts what the runtime can actually do with a given portable artifact on the current machine and under the current policy state.

It is not just model metadata. It is:

- a validation surface
- a host UX surface
- a scheduler hint surface
- a policy and provenance surface

## Required Top-Level Fields

| Field | Purpose |
| --- | --- |
| `model_id` | Stable runtime identifier for the artifact instance. |
| `artifact_digest` | Identifies the portable artifact, not the build cache. |
| `family` | High-level family such as `ltx`, `sdxl`, `whisper`, `qwen-vlm`. |
| `family_variant` | Variant such as `fast`, `distilled`, or provider-converted subtypes. |
| `tasks` | Supported task IDs. |
| `modalities_in` | Input modalities. |
| `modalities_out` | Output modalities. |
| `constraints` | Hard input constraints and formulas. |
| `conditioning` | Supported conditioning types and high-level semantics. |
| `profiles_by_task` | Supported profiles by task. |
| `streaming` | Event and partial-output support. |
| `artifacts_out` | Runtime-managed artifact formats that can be emitted. |
| `scheduler_class` | Scheduler class used for admission and stage policy. |
| `hardware_tiers` | Machine-fit guidance and limitations. |
| `dependencies` | External or platform-managed dependencies such as encoders or native helpers. |
| `policy` | License, access state, and remote-code facts. |
| `extensions_schema` | Family-specific extension namespace and version. |

## Constraints

`constraints` must express machine-checkable rules instead of vague notes.

Examples:

- multiples of 32
- frame-count formulas such as `8n+1`
- maximum number of reference images
- supported aspect-ratio profiles
- whether audio duration must match video duration

If the runtime

*[truncated — see source for full prompt]*