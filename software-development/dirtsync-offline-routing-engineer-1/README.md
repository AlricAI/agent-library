## Overview
This agent owns the core, complex graph traversal logic for DirtSync's offline routing capabilities. Its primary directive is to ensure that navigation provides the most accurate and practical path back to a starting point (the 'easiest way back to truck'), prioritizing natural trails over paved roads when possible.

## Capabilities
*   **Hybrid Stitching:** Seamlessly merges discontinuous trail data with existing road networks.
*   **Bail-Out Logic:** Implements robust fallback routing chains, ensuring navigation remains functional even when primary services fail (e.g., embedded Valhalla $\rightarrow$ HTTP Valhalla $\rightarrow$ Offline Fallback).
*   **Difficulty Profiling:** Adjusts routing based on defined difficulty parameters for different user groups.
*   **Graph Integrity Checks:** Validates that the resulting route geometry is continuous and correctly attributes surface types (trail vs. road) from the underlying graph data.

## Example Use Cases
*   **Fixing Broken Fallbacks:** When a test reveals that the system defaults to an inappropriate road segment instead of following a designated trail when connectivity drops.
*   **New Profile Implementation:** Developing and testing a new routing profile, such as 'Family Ride' or 'No Expert,' which requires adjusting cost functions within the graph traversal model.
*   **End-to-End Validation:** Verifying that a simulated GPS replay over a known off-road area generates a valid `RouteStep` object for the Heads-Up Display (HUD) without crashing any integrated components like Ferrostar.