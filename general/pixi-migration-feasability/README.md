# Pixi Migration Feasability

> ## Summary
- **Status:** Exploratory assessment
- Migrating the canvas-based renderer to WebGL via Pixi.js is viable but requires a multi-phase refact

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# PIXI Migration Feasibility

## Summary
- **Status:** Exploratory assessment
- Migrating the canvas-based renderer to WebGL via Pixi.js is viable but requires a multi-phase refactor to preserve the current scene element system, binding infrastructure, and tooling hooks.

## Current Rendering Architecture
- `MIDIVisualizerCore` owns the HTML canvas, animation loop, and delegates rendering to a `ModularRenderer` instance that iterates over render objects and issues imperative Canvas2D calls.【F:src/core/visualizer-core.ts†L12-L188】【F:src/core/render/modular-renderer.ts†L10-L30】
- Visual content is built by the `SceneRuntimeAdapter`, which mirrors scene store state, instantiates scene elements through the registry, and asks each element to emit render objects ordered by z-index.【F:src/state/scene/runtimeAdapter.ts†L29-L209】
- Scene elements wrap property bindings, macro integration, and cached bounds computations before packaging child render objects inside an `EmptyRenderObject` container that applies transforms, opacity, and anchor math uniformly.【F:src/core/scene/elements/base.ts†L19-L415】【F:src/core/render/render-objects/empty.ts†L11-L129】
- Interaction overlays (selection boxes, guides, handles) are drawn directly on the same 2D context after the scene render, relying on Canvas APIs such as `setLineDash`, `strokeRect`, and path drawing.【F:src/core/visualizer-core.ts†L360-L520】
- Export utilities reuse the canvas renderer to synthesize image data, data URLs, or blobs synchronously on the CPU.【F:src/core/render/modular-renderer.ts†L32-L80】

## Canvas Feature Surface Area
- Primitive render objects depend on Canvas-specific features: gradient-free fills, shadows, rounded path drawing, and alpha stacking for rectangles; text relies on `CanvasRenderingContext2D` font metrics, shadows, and stroke/fill layering; images are drawn via `drawImage` with clipping for cover mode and placeholders for loading states.【F:src/core/render/render-objects/rectangle.ts†L3-L153】【F:src/c

*[truncated — see source for full prompt]*