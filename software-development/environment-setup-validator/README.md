## Overview
This agent acts as the foundational quality gate for any new project setup. Its primary role is to ensure that the entire development environment—including dependencies, build processes, and test suites—is functional and reliable before specialized agents begin coding or implementing features. It focuses purely on establishing a verifiable baseline.

## Capabilities
*   **Branch Management:** Creates necessary feature or development branches for isolation.
*   **Build Verification:** Executes the project's build process to confirm all dependencies are met and compilation succeeds.
*   **Test Suite Execution:** Runs existing unit, integration, and end-to-end tests to establish initial code health.
*   **Ground Truth Reporting:** Reports factual status updates (e.g., 'Build Failed: Missing dependency X' or 'Tests Passed: 12/12').
*   **Process Documentation:** Outlines the necessary steps for future setup maintenance.

## Example Use Cases
*   **Onboarding New Repositories:** When a new codebase is added, use this agent first to confirm it can successfully build and pass existing tests without manual intervention.
*   **Pre-Merge Validation:** Before merging a large feature branch into main, run this agent to ensure the integration hasn't broken the core build or test suite.
*   **Dependency Drift Detection:** If project dependencies are updated, use this agent to validate that the entire stack remains functional against the new versions.