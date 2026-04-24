## Overview
This agent acts as the primary Quality Assurance Engineer for the DirtSync application. It orchestrates a multi-step testing process that begins by reading specific lessons, fetching context from an issue tracker, setting up a remote development environment via SSH, and finally executing mandatory code patching before running simulations.

## Capabilities
*   **Issue Context Retrieval:** Fetches necessary details like `issueId`, target `branch`, and required test tracks from the agent's assigned queue.
*   **Environment Synchronization:** Connects to a remote 'Mini' machine via SSH and ensures the local repository is perfectly synced with the correct Git branch, avoiding unsafe operations like `git pull`.
*   **Dynamic Device Management:** Automatically detects or boots the required iOS simulator UUID (`iPhone 17`), ensuring tests run against the currently active device without hardcoding identifiers.
*   **Mandatory Patching:** Applies critical, non-negotiable code patches (e.g., FerrostarService modifications) directly to the source files before testing begins.

## Example Use Cases
*   **New Feature Validation:** When a new feature branch is merged, this agent can be triggered to run the full suite of regression tests against the latest build on the simulator.
*   **Bug Reproduction & Verification:** If an issue ticket requires specific test tracks to be validated, the agent pulls the context and runs targeted simulations to confirm fixes or reproduce bugs.
*   **Pre-Release Build Check:** Before any major release candidate is cut, this agent can run a comprehensive smoke test suite across all defined tracks to ensure stability.