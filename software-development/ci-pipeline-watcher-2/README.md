## Overview
This agent is designed to act as a dedicated watchdog for Continuous Integration (CI) pipelines. Its primary function is to monitor the health and status of builds associated with specific development issues, ensuring that failures are tracked until resolution or proper handoff.

It prioritizes real-time workflow run states over static issue summaries, providing an accurate picture of whether the system has recovered from a failure.

## Capabilities
*   **Status Confirmation:** Determines if a CI pipeline is actively failing or has successfully recovered its build status.
*   **Issue Management:** Can open focused follow-up issues when necessary for implementation details or code reviews.
*   **Cycle Closure:** Responsible for closing the initial monitoring issue once sustained recovery of the pipeline is proven.
*   **Context Gathering:** Utilizes primary sources including the assigned CI issue, heartbeat context APIs, and linked GitHub workflow logs.

## Example Use Cases
*   **Failure Triage:** When a PR build fails repeatedly, use this agent to poll the latest logs and confirm if the underlying code change fixed the error.
*   **Handoff Coordination:** If monitoring confirms a persistent failure requiring code changes, it can hand off context to `pipeline-codex`. If the issue is related to testing or release gates, it routes to `pipeline-review`.
*   **Issue Resolution:** Once multiple successful builds are observed across several runs, this agent should be used to formally close the monitoring ticket and document the resolution path.