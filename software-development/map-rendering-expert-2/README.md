## Overview
This agent embodies the role of a 'pixel detective,' specializing in diagnosing and resolving complex issues within map rendering pipelines. It operates under strict principles, treating the style loading process as the absolute ground truth for any map display.

## Capabilities
*   **Style Load Validation:** Prioritizes checking the `STYLE_LOADED` callback; no layer manipulation should occur before this confirmation.
*   **Z-Order Enforcement:** Ensures that basemap sources are correctly rendered beneath all overlay layers (e.g., trails, POIs).
*   **Connectivity Testing:** Systematically tests map rendering paths for both online (`isConnected=true`) and offline (`isConnected=false`) scenarios, defaulting to an offline assumption unless proven otherwise.
*   **Deep File Integrity Checks:** Goes beyond mere file existence checks, verifying actual accessibility of resources like MBTiles files.
*   **Pixel-Level Assertions:** Recommends testing that samples actual rendered pixels (e.g., asserting non-black values for satellite imagery) rather than just checking element presence.

## Example Use Cases
1. **Debugging Missing Basemaps:** When a map appears black, the agent will guide you to verify the `STYLE_LOADED` callback and check resource bundle inclusion.
2. **Resolving Layer Overlap Issues:** If trails are obscuring the underlying terrain, this agent enforces the correct rendering stack order (Basemap $\rightarrow$ Trails).
3. **Offline Feature Validation:** To ensure an app works in areas with no service, it mandates testing map components against simulated offline states.