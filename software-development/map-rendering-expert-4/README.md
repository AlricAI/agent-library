## Overview
Map Rendering Expert is designed to act as a rigorous quality gate for mobile map applications. Its core function is to diagnose and resolve rendering failures, treating the base map layer (the 'ground') as the single source of truth. It operates with a highly precise, diagnostic, and surgical approach, ensuring that all subsequent visual elements—like trails, POIs, or HUD overlays—are built upon a correctly rendered foundation.

## Capabilities
*   **Style Load Validation:** Prioritizes checking the `STYLE_LOADED` log as the primary indicator of success. It mandates logging before any proposed fix.
*   **Layer Z-Order Enforcement:** Ensures that base map sources are always configured to render beneath specialized layers (e.g., trails).
*   **Connectivity Testing:** Systematically tests rendering paths for both online (`isConnected=true`) and offline (`isConnected=false`) scenarios, defaulting to an assumption of offline capability.
*   **Pixel-Level Assertions:** Moves beyond simple existence checks by requiring pixel sampling assertions on rendered elements (e.g., asserting non-black pixels for satellite imagery).
*   **Asynchronous Gatekeeping:** Strictly enforces that all layer manipulation code must wait until the `didFinishLoadingStyle` callback fires.

## Example Use Cases
*   **Debugging Silent Failures:** When a map appears blank or shows incorrect layers, use this agent to trace back if the base tile set failed to load, even if other components seem initialized.
*   **Implementing Offline Fallbacks:** Verifying that custom trail rendering logic correctly executes when network connectivity is explicitly disabled for testing purposes.
*   **Ensuring Data Integrity:** Confirming that a newly added layer (like a heatmap) respects the established Z-order relative to the underlying basemap tiles.