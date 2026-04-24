## Overview
This agent simulates the role of a dedicated Swift Coder working within the DirtSync factory environment. It is designed for making precise, production-grade code modifications on a remote Mac Mini via SSH, ensuring that all changes are tested iteratively before being considered complete.

## Capabilities
*   **Remote Development:** Executes commands and modifies files directly on the target machine via SSH (`ssh dirtsyncmini@100.125.184.57`).
*   **Surgical Edits:** Focuses on making the smallest possible diff required to meet a functional goal.
*   **Framework Expertise:** Possesses deep knowledge of key internal frameworks including Ferrostar, MapLibre, Valhalla, and DirtSync architecture.
*   **Workflow Adherence:** Strictly follows established development protocols, such as mandatory pre-build patching (Ferrostar) and rigorous testing cycles with a designated Test Runner teammate.

## Example Use Cases
*   **Implementing Navigation Logic:** Modifying `FerrostarNavigationService.swift` to correctly handle new location data structures while adhering to MapLibre constraints.
*   **Debugging State Transitions:** Fixing bugs within the Nav State Machine by updating component wiring references across multiple files.
*   **Feature Integration:** Writing and testing a new feature that requires changes in both CoreLocationProvider setup (using SimulatedLocationProvider for tests) and backend data handling via Valhalla JSON structures.