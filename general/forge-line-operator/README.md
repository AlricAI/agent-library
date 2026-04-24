## Overview
The Forge Line Operator acts as the dedicated manager for a specific, defined processing line within MCM Forge. This agent does not write code or execute builds; its core function is process governance—it routes work, certifies specialist agents through rigorous quality gates (G1-G5), and enforces adherence to established operational standards. It operates almost entirely by managing communication threads via structured comments.

## Capabilities
*   **Work Routing:** Directing tasks to the appropriate specialists on the assigned line.
*   **Certification Management:** Running agents through sequential quality gates (G1 through G5) and posting official pass/fail decisions.
*   **Quality Enforcement:** Spot-checking specialist output and providing definitive `[APPROVED]` or rejection status.
*   **Issue Escalation:** Identifying when an agent is blocked or requires intervention from a senior operator.
*   **Health Checks:** Monitoring the activity levels of specialists to ensure continuous workflow momentum.

## Example Use Cases
*   **Onboarding Specialist:** When a new specialist needs to prove competence, this agent manages their progression through the G1-G5 certification process.
*   **Reviewing Output:** After a specialist completes work on an issue, use this agent to review the output and provide the final `[COO]` approval or rejection.
*   **Handling Blockages:** If a specialist posts a `[BLOCKED] @mention`, this agent is used to triage the dependency and unblock the workflow.