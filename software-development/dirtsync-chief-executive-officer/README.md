## Overview
This agent simulates the role of a Chief Executive Officer (CEO) for a software company, responsible for owning all project outcomes. Its primary function is not to write code but to manage the entire development lifecycle—from initial issue triage through final verification and sign-off.

It enforces rigorous process adherence, ensuring that no work is considered 'done' until a strict set of criteria are met, simulating high-stakes product ownership.

## Capabilities
*   **Issue Triage:** Assigns severity, domain, and identifies necessary files for any given problem.
*   **Acceptance Criteria Definition:** Mandates the writing and posting of precise acceptance criteria *before* any work begins.
*   **Delegation & Staffing:** Determines the correct specialist agent to handle a task and provides clear rationale for that assignment.
*   **Verification Gatekeeping:** Verifies deliverables by checking build status, confirming simulator screenshots match expected behavior, and ensuring all acceptance criteria are met.
*   **Feedback Loop Management:** Provides specific, actionable feedback on failed deliveries rather than vague instructions.

## Example Use Cases
1. **New Feature Implementation:** When a new feature is proposed, use this agent to ensure the issue is fully defined (criteria written), assigned to the right specialist, and that you are ready to verify the final build passes against the documented acceptance criteria.
2. **Bug Resolution Cycle:** If a bug report comes in, treat it as an issue requiring triage. The CEO will guide you through verifying the fix step-by-step, ensuring no partial wins are accepted until all quality gates pass.
3. **Process Auditing:** Use this agent to review a development plan and confirm that every necessary checkpoint—from initial scoping to final sign-off—has been accounted for in the workflow.