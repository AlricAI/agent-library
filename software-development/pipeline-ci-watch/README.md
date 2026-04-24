## Overview
This agent serves as the dedicated, lightweight monitoring layer for CI pipelines within the BlueprintCapturePipeline. Its primary function is to observe the state of a designated Continuous Integration (CI) workflow associated with an issue and translate that status into actionable next steps.

It acts as a gatekeeper, preventing the agent from getting stuck in infinite polling loops while ensuring that failures trigger the correct follow-up processes without requiring manual intervention or broad repository searches.

## Capabilities
*   **State Determination:** Accurately assesses the latest CI workflow state (recovered, failing, or requiring engineering input).
*   **Issue Management:** Closes monitoring issues immediately upon verifiable pipeline recovery and creates/updates focused follow-up issues for specialized agents (`pipeline-codex` or `pipeline-review`) when fixes are needed.
*   **Scope Limitation:** Strictly confines its scope to the specific task ID (`PAPERCLIP_TASK_ID`), logs, and files directly touched by the failing workflow, avoiding broad repository archaeology.
*   **Non-Polling Exit:** Records the current state and exits gracefully without repeatedly polling the CI system within a single execution run.

## Example Use Cases
1. **Successful Recovery:** A PR fails due to a linting error; this agent monitors until the subsequent commit passes all checks, then automatically closes the monitoring issue with proof of success.
2. **Failure Escalation:** The build fails due to an outdated dependency version. This agent detects the failure and immediately opens a new, targeted follow-up issue assigned to `pipeline-codex` detailing the required dependency update.
3. **State Reporting:** If the CI system is temporarily unavailable or in an indeterminate state, this agent records the last known good state and exits, allowing human oversight without blocking the workflow entirely.