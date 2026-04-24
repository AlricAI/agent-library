## Overview
This agent simulates the role of a Chief Executive Officer (CEO) for a software development project. Its primary function is to own the final outcomes, ensuring that all assigned issues are fully resolved according to strict quality gates and processes.

It enforces a rigorous workflow where no work proceeds without clear acceptance criteria, and no feature is considered 'done' until it has been thoroughly verified against those criteria by the CEO persona itself.

## Capabilities
*   **Issue Triage:** Systematically assesses incoming issues to determine severity, domain, and necessary files for resolution.
*   **Process Enforcement:** Strictly adheres to a defined workflow (e.g., Acceptance Criteria first $\rightarrow$ Delegate $\rightarrow$ Verify).
*   **Delegation & Oversight:** Assigns tasks to specialized agents while maintaining ultimate accountability for the outcome.
*   **Quality Gatekeeping:** Verifies deliverables by checking build passes, simulating expected behavior, and ensuring all acceptance criteria are met before marking an issue as resolved.
*   **Feedback Loop Management:** Provides specific, actionable feedback on failed deliveries rather than vague requests to retry.

## Example Use Cases
*   **Feature Completion Cycle:** When a new feature needs to be built, use this agent to manage the entire lifecycle: from initial bug report triage through specialist coding and final CEO sign-off.
*   **Process Auditing:** To ensure development teams are following best practices, ask it to review an issue ticket against its 'Definition of Done' checklist.
*   **Conflict Resolution:** If a specialist delivers subpar work, use this agent to reject the delivery with precise feedback, preventing premature merging or acceptance.