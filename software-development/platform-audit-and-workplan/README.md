# PLATFORM AUDIT AND WORKPLAN

> ## 1) Code/ABI discovery summary

### 1.1 VisualParameters and Embodiment ABI
- `VisualParameters` carries render-facing fields via `visual_parameters

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Aetherium Genesis Platform Audit + Work Plan

## 1) Code/ABI discovery summary

### 1.1 VisualParameters and Embodiment ABI
- `VisualParameters` carries render-facing fields via `visual_parameters`: `base_shape`, `turbulence`, `particle_density`, `color_palette`, and `flow_direction`.
- `EmbodimentContract` carries UI-driving inputs under `temporal_state`, `cognitive`, and `intent`:
  - Inputs: `phase`, `stability`, `duration_ms`, `effort`, `uncertainty`, `latency_factor`, `category`, `purity`.
  - Output path: `EmbodimentAdapter.translate(...) -> VisualParameters`.

### 1.2 `intent_vector` contract surface
- Bus contract `formation.schema.json` requires `intent_vector` + `motion_class`.
- Kernel publishes `intent_vector` into event extensions and reconstructs it for subscribers.

### 1.3 GunUI responsibility check
- Spec says visual output must be truthful, state-bound, and avoid decorative use:
  - Embodiment Contract: "observable truth", "No Smoothing" at contract layer, and `IDLE` should minimize to "Pilot Light".
  - Light Protocol: rejects decoration/media usage.
  - Goal Lock: "Light is Language, Not Effect", state-first sequence.
- Current GunUI implementation (`src/frontend/public/gunui/index.html`) is stateful but has legacy fallbacks that can over-render:
  - On `LOGENESIS_RESPONSE`/`LightInstruction`, it maps to hardcoded default `{cloud, #FFFFFF, turbulence=0.1}`.
  - In `applyVisualParams`, any non-manifestation mode can force `RESONATING` from `IDLE/PROCESSING`, which may reduce strict "pilot light" behavior.

## 2) Color and mood analysis

## 2.1 AM-UI color system reference status
No file explicitly named "AM-UI Color System" was found in this repository. The closest normative color/state references are:
1. `docs/EMBODIMENT_CONTRACT.md` (temporal + intent mapping),
2. `docs/LIGHT_PROTOCOL.md` (color as uncertainty/context signal),
3. `docs/ENTROPY_ECONOMY_TECHNICAL_SPEC_TH.md` (Predictable/Divergent/Chaotic mapping),
4. `src/backend/genesis_core/l

*[truncated — see source for full prompt]*