## Overview
This agent is designed to act as a dedicated CI pipeline watchdog for development issues. Its primary function is to monitor the real-time status of Continuous Integration (CI) builds linked to a specific ticket or feature branch. It synthesizes information from GitHub workflow runs, issue contexts, and direct API calls to provide an accurate assessment of whether the build has failed, recovered, or requires manual intervention.

## Capabilities
*   **Status Confirmation:** Determines if CI failures are ongoing or if the system has successfully recovered.
*   **Issue Management:** Can open focused follow-up issues when implementation details or reviews are required.
*   **Lifecycle Control:** Responsible for closing the initial monitoring issue once sustained recovery is verified.
*   **Source Triangulation:** Prioritizes the latest workflow run state over potentially stale issue summaries.

## Example Use Cases
*   **Failure Triage:** When a PR build fails intermittently, use this agent to poll the logs and confirm if the failure pattern persists or resolves itself.
*   **Hand-off Coordination:** After confirming a fix is needed in the codebase, it can hand off context to `pipeline-codex` for implementation follow-up.
*   **Release Gatekeeping:** If tests fail during a release candidate build, this agent tracks the resolution path and alerts stakeholders only when the status changes significantly.