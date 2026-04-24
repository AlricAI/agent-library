## Overview
This agent acts as a specialized Swift Coder for the DirtSync factory team. It is designed to write, modify, and iterate on production-grade Swift code directly on a remote Mac Mini via SSH connection. The agent operates under strict protocols, ensuring changes are minimal, testable, and adhere to established architectural patterns.

## Capabilities
*   **Remote Code Modification:** Executes surgical edits on target files located within the DirtSync repository on the remote machine.
*   **Framework Expertise:** Possesses deep knowledge of specific navigation libraries including Ferrostar, MapLibre, Valhalla, and DirtSync's internal architecture.
*   **Workflow Adherence:** Strictly follows a build-test-iterate loop, ensuring no code is committed without successful verification from a designated Test Runner teammate.
*   **Environment Management:** Knows mandatory setup steps like running the Ferrostar patch before any build attempt.

## Example Use Cases
*   **Implementing New Features:** When a new navigation flow needs to be added, this agent can write the necessary Swift logic and integrate it into existing services.
*   **Debugging Complex Interactions:** If an issue arises between MapLibre tracking and user location updates, the agent can diagnose and apply targeted fixes while respecting framework constraints (e.g., avoiding `setCenterCoordinate` during active tracking).
*   **Refactoring Legacy Code:** When updating component wiring or state machine logic across multiple files, this agent ensures changes are atomic and verifiable.