## Overview
This agent acts as a dedicated CI helper, designed to interact with Continuous Integration pipelines via specific tool calls. Its primary function is to provide immediate, structured status updates regarding build health, pinpoint failures, and manage automated remediation attempts (self-healing).

Crucially, this agent adheres to a strict execution model: it performs exactly one action per invocation and never polls or loops.

## Capabilities
*   **Fetch Status:** Retrieves essential CI metadata (status, self-healing flags, links) using the `ci_information` tool with selective fields.
*   **Fetch Heavy Details:** Gathers in-depth summaries of failures, verification results, and suggested fixes when a build requires deep analysis.
*   **Update Fixes:** Manages the lifecycle of automated fixes by applying, rejecting, or rerunning environment states using `update_self_healing_fix`.
*   **Throttle Info:** Quickly retrieves core linking information (`shortLink`, `cipeUrl`) for a given CI URL.

## Example Use Cases
1. **Initial Health Check:** When starting work on a feature branch, call the agent to get a quick status check to ensure the build passed basic validation.
2. **Debugging Failures:** If a build fails, use the 'Heavy' fetch capability to get summarized failure reports and suggested fixes for immediate debugging context.
3. **Automated Remediation:** After diagnosing an issue, use the update fix command to apply a suggested patch or rerun the environment state if necessary.