# ARCHITECTURE

> ## Domain Boundaries

Logical domains keep responsibilities isolated:

-   **animation/** – Stateless animation primitives for piano rolls
-   **core/

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Architecture Overview

## Domain Boundaries

Logical domains keep responsibilities isolated:

-   **animation/** – Stateless animation primitives for piano rolls
-   **core/** – Runtime engine logic (scene runtime adapter, rendering, timing, playback clock, resource management).
-   **state/** – Zustand stores, selectors, and middleware. Hosts the canonical timeline and scene stores plus command/undo infrastructure.
-   **workspace/** – Components for the main workspace ui
-   **math/** – Generic math, geometry, and numeric helpers.
-   **export/** – Code for export functions
-   **utils/** – Shared utilities (logging, throttling, feature flag helpers, etc.).

Music theory helpers and MIDI parsing live under `core/midi/` alongside the playback/timeline stack so the runtime can consume them without depending on UI code.

## Canonical Time & Scene Authority

-   Tick-based timeline (`timelineStore`) remains the source of truth for transport, tempo, and note scheduling. Seconds/beats are derived through shared timing utilities when needed.
-   `sceneStore` holds all scene elements, bindings, macros, interaction state, and persistence metadata. UI components and runtime adapters read from this store instead of mutating legacy globals.
-   The command gateway (`dispatchSceneCommand`) is the only sanctioned mutation entry point for scene data. It applies store mutations and feeds undo/telemetry instrumentation for observability.
-   Undo middleware spans both timeline and scene domains so transactions remain atomic across stores when commands mutate multiple slices.

## Data Flow

1. User input (UI, hotkeys, transport) dispatches commands or store actions.
2. Command gateway/store actions update Zustand state and emit mutation metadata.
3. Memoized selectors derive ordered elements, macro assignments, timing windows, etc.
4. Runtime layers (`SceneRuntimeAdapter`, playback clock) consume derived data to render frames or drive audio/MIDI output.
5. Export pipeline leverag

*[truncated — see source for full prompt]*