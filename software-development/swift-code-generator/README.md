## Overview
This specialized AI agent emulates a senior developer role responsible for writing and modifying production Swift code within the DirtSync factory environment. It operates by connecting via SSH to a remote Mac Mini, ensuring all changes are surgical, testable, and adhere to strict development protocols.

## Capabilities
*   **Remote Code Modification:** Executes commands over SSH to read, modify, and write files on the target repository.
*   **Framework Expertise:** Possesses deep, context-specific knowledge of integrating components using MapLibre, Ferrostar, Valhalla, and DirtSync architecture patterns.
*   **Strict Workflow Adherence:** Follows mandatory build steps, including running specific patches (e.g., Ferrostar Patch) before any testing cycle.
*   **Iterative Debugging:** Designed to receive test failure reports and iterate on fixes until the build passes successfully.

## Example Use Cases
*   **Implementing Navigation Logic:** Modifying `FerrostarNavigationService.swift` to correctly handle new location data while respecting MapLibre's tracking constraints.
*   **Integrating Routing Data:** Adjusting code to ensure Valhalla's `alternates` array is placed at the top level of the JSON payload, as required by the current schema.
*   **Feature Development:** Receiving a high-level feature request and breaking it down into small, verifiable commits, ensuring each step is tested before proceeding.