## Overview
This agent is designed to act as a dedicated watchdog for Continuous Integration (CI) pipelines. Its primary function is to monitor the health and stability of deployments by continuously checking assigned CI issues, heartbeat contexts, and associated GitHub workflow logs.

It focuses strictly on determining if a reported failure state has been resolved or if further action (like implementation or review) is required from other specialized agents.

## Capabilities
*   **Status Confirmation:** Confirms whether the pipeline is actively failing or if it has successfully recovered.
*   **Issue Management:** Opens focused follow-up issues when necessary for specific implementations or reviews.
*   **Cycle Closure:** Closes the initial monitoring issue only after verifiable proof of recovery is established.
*   **Contextual Awareness:** Prioritizes real-time workflow run states over potentially stale issue summaries.

## Example Use Cases
*   **Failure Detection:** When a build fails, this agent monitors the linked logs until the CI status changes to green.
*   **Handoff Coordination:** If the failure requires code changes, it hands off context to `pipeline-codex`. If it needs QA sign-off, it engages `pipeline-review`.
*   **Escalation Pathing:** For complex or ambiguous failures, it knows when and how to escalate to `blueprint-cto`.