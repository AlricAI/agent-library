# Rendering Writeup 1

> ## High-level flow

-   **UI entry point:** `RenderModal` (`src/workspace/layout/RenderModal.tsx`) gathers export preferences and kicks off either a P

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Rendering pipeline walkthrough (RenderModal ➜ encoded output)

## High-level flow

-   **UI entry point:** `RenderModal` (`src/workspace/layout/RenderModal.tsx`) gathers export preferences and kicks off either a PNG sequence export or an MP4 video render.
-   **Context orchestration:** The modal calls `exportSequence` / `exportVideo` exposed by `VisualizerContext`. That context is responsible for showing progress UI, deriving timeline ranges, and delegating to the appropriate exporter instance.
-   **Exporter instances:** `useVisualizerBootstrap` lazily loads heavy modules and instantiates `ImageSequenceGenerator`, `VideoExporter`, and (indirectly) `AVExporter`, all sharing a single `MIDIVisualizerCore` instance bound to the workspace canvas.
-   **Frame production:** Both exporters drive the visualizer deterministically with an `ExportClock`, rendering frames via `MIDIVisualizerCore.renderAtTime`, which in turn delegates to `ModularRenderer` and the scene graph runtime.
-   **Encoding / packaging:**
    -   PNG exports stream frames to blobs and zip them with JSZip before triggering a download.
    -   MP4 exports encode frames with Mediabunny’s WebCodecs wrapper and, when possible, ask `AVExporter` to mux in an offline audio mix.

## Detailed path

### 1. `RenderModal`: collecting intent and dispatching a job

-   Tracks a mix of legacy (`qualityPreset`, `bitrate`) and newer (`videoCodec`, `videoBitrateMode`, advanced audio controls) fields in local state.
-   On **Start**, it:
    1. Persists the chosen parameters back into the global `exportSettings` via `setExportSettings`, so future runs share new defaults.
    2. Calls either `exportSequence` or `exportVideo` from `VisualizerContext` with an override payload that mirrors the local state (including the legacy bitrate fields for backward compatibility).
-   It also preloads codec capability data (`mediabunny` helpers) and lazily registers the MP3 encoder when the user picks that codec.

### 2. `VisualizerCont

*[truncated — see source for full prompt]*