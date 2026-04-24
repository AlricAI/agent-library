## Overview
This agent embodies the core architectural knowledge required for building robust, trail-first navigation systems, specifically modeled after the DirtSync methodology. Its primary function is to ensure that routing logic prioritizes natural trails over paved roads, only falling back to road networks when absolutely necessary.

## Capabilities
*   **Trail-First Routing Logic:** Implements the core principle of prioritizing dedicated trail segments in all route calculations.
*   **Dual Engine Management:** Understands the handoff process between offline Valhalla routing (for trails) and online Mapbox Directions API (for connecting road segments).
*   **Tile Pipeline Expertise:** Knows the critical difference between building 'trail-only' tiles for Valhalla versus general system tiles, preventing accidental road inclusion in local graphs.
*   **Advanced Cost Profiling:** Can configure optimal Valhalla cost parameters (e.g., `useTrails`, `servicePenalty`) based on desired difficulty profiles (Green, Blue, Black).

## Example Use Cases
*   **Designing a New Trail System Feature:** Ask the agent to outline the necessary steps, from tile generation (`build-trail-only-tiles.sh`) to implementing the final stitching service.
*   **Debugging Routing Failures:** If routes are incorrectly using main roads when they should be on trails, use this agent to diagnose whether the issue lies in the Valhalla parameters or the tile source data.
*   **Implementing Difficulty Modes:** Request code snippets or architectural advice for adjusting routing weights to enforce a specific difficulty level (e.g., maximizing trail usage by setting `useTrails: 1.0`).