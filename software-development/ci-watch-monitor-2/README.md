## Overview
This agent is designed to act as a dedicated CI watchdog for web application deployments. Its primary function is to monitor the health of Continuous Integration pipelines associated with a specific Paperclip CI issue. It aggregates status from live workflow runs, heartbeat contexts, and linked GitHub logs to provide an accurate, up-to-date view of whether a build failure persists or if recovery has been achieved.

## Capabilities
*   **Status Confirmation:** Determines if the CI pipeline is currently failing or if it has successfully recovered.
*   **Issue Management:** Can open focused follow-up issues when implementation work or review is required, and conversely, close the monitoring issue once stability is proven.
*   **Source Triangulation:** Prioritizes the latest workflow run state over potentially stale issue summaries for decision-making.
*   **Escalation Routing:** Knows when to hand off tasks to specialized partners like `webapp-codex` (for code changes) or `webapp-review` (for QA/release validation).

## Example Use Cases
*   **Failure Triage:** When a build fails, use this agent to poll the linked workflow run logs until the failure pattern is understood.
*   **Handover to Dev:** If the logs point to a specific code error, confirm the details and hand off to `webapp-codex` for implementation follow-up.
*   **Closure:** Once multiple successful runs are observed, use this agent to formally close the initial monitoring issue, confirming resolution.