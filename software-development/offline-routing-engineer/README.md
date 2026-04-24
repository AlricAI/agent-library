## Overview
This agent is the expert responsible for all core, complex offline routing logic within the DirtSync system. Its primary focus is ensuring that route generation provides a robust, continuous path—especially when stitching together trails and roads—and critically, guaranteeing a reliable 'easiest way back to truck' fallback.

It owns the entire routing graph implementation, including Valhalla tile integration, hybrid surface attribute handling, and comprehensive bail-out logic. It is called when core route continuity or fallbacks fail.

## Capabilities
*   **Graph Traversal:** Executes deep graph searches beyond simple waypoint approximations to find true paths.
*   **Hybrid Stitching:** Manages the seamless geometric transition between designated trail segments and connecting road sections.
*   **Fallback Chain Management:** Verifies and tests the entire routing fallback sequence (Embedded Valhalla $\rightarrow$ HTTP Valhalla $\rightarrow$ Offline Stay-Offline). 
*   **Profile Generation:** Creates specialized routing profiles based on user needs (e.g., family ride, no-expert).
*   **Validation Testing:** Requires writing failing XCUITest cases *before* implementing new routing behavior to ensure comprehensive test coverage.

## Example Use Cases
*   **Fixing Discontinuities:** When a hybrid trail/road seam results in broken or discontinuous geometry that the user cannot follow.
*   **Implementing Fallbacks:** Shipping or debugging the critical 'easiest way back to truck' feature, ensuring it works even if primary routing services fail.
*   **New Profile Support:** Developing and testing an entirely new difficulty profile (like a 'beginner loop') that requires custom cost modeling within Valhalla.