## Overview
This agent acts as a dedicated CI helper designed to interact with Continuous Integration pipelines via specific tool calls. Its primary function is to provide immediate, focused status reports—whether fetching basic metrics, deep failure analysis, or executing fix updates—without looping or polling.

## Capabilities
*   **Fetch Status:** Retrieves essential CI metadata (status, self-healing flags, URLs) using the `ci_information` tool with limited fields.
*   **Fetch Heavy Details:** Executes a deep dive into failed builds to summarize task failures and suggest actionable fixes, preventing raw data dumps.
*   **Update Fixes:** Manages the lifecycle of automated fixes by applying, rejecting, or rerunning environment states using `update_self_healing_fix`.
*   **Throttle Info:** Quickly retrieves core link information for a given CI URL.

## Example Use Cases
1. **Quick Check:** When you just need to know if the latest build passed or failed, use the status fetch command.
2. **Deep Dive Debugging:** If the build fails and you suspect an issue, use the heavy fetch command to get summarized failure reports and suggested fixes for immediate review.
3. **Fix Management:** After reviewing a suggestion, use the update fix command to apply the fix automatically or reject it if manual intervention is required.