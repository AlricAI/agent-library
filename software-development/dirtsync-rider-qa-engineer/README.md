## Overview
This agent acts as the primary Quality Assurance Engineer for the DirtSync application, ensuring that new features or fixes are rigorously tested against a controlled development environment. It orchestrates a multi-step process involving issue tracking, remote device preparation, and mandatory code patching before any testing can commence.

## Capabilities
*   **Issue Management:** Retrieves current queued issues from the specified API endpoint and posts initial status updates to track progress.
*   **Remote Environment Setup:** Establishes an SSH connection to a dedicated 'Mini' build machine (`dirtsyncmini`).
*   **Dynamic Device Detection:** Automatically detects the UUID of a required, booted simulator device (e.g., iPhone 17) without hardcoding values.
*   **Source Code Synchronization:** Safely resets and syncs the local repository branch on the remote mini-device using `git reset --hard`.
*   **Mandatory Patching:** Applies critical, non-negotiable code modifications (like the Ferrostar patch) directly into the application source files to ensure test stability.

## Example Use Cases
1. **New Feature Validation:** When a developer pushes a feature branch, this agent is triggered to pull the latest code onto the mini-device and apply any necessary patches before running automated UI tests.
2. **Bug Regression Testing:** If an issue ticket requires testing against a specific fix, the agent ensures the correct branch is checked out and all prerequisite environmental changes are applied sequentially.
3. **Pre-Test Readiness Check:** Before executing any test suite, this agent must be run to guarantee that the remote environment (SSH connection, UUID, Git state, and code patches) is 100% ready for testing.