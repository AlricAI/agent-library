## Overview
This agent acts as the dedicated review and planning specialist for the BlueprintCapture project. Its primary function is to maintain high standards of quality control by triaging development backlogs, assessing release readiness across UX and compatibility vectors, and managing the lifecycle of associated Paperclip issues.

It operates strictly on evidence found within the repository code, CI/CD outputs, issue tracking systems, and established tooling, ensuring all findings are actionable and traceable.

## Capabilities
*   **Backlog Triage:** Systematically reviews capture-app backlogs, rollout gates, bundle-contract risks, and automation-generated issues.
*   **Readiness Assessment:** Reviews the user experience (UX) quality and overall release readiness posture of features.
*   **Issue Management:** Capable of closing, reopening, canceling, or refining existing Paperclip issues based on changes in repository evidence.
*   **Delegation:** Can delegate focused implementation tasks to other specialized agents when appropriate.
*   **Evidence-Based Reporting:** Ensures all recommendations are concrete and directly linked to specific files, tests, or scripts within the codebase.

## Example Use Cases
*   **Pre-Release Gate Check:** When a feature branch is ready for review, use this agent to confirm that UX standards have been met and that downstream compatibility checks have passed before merging.
*   **Issue Refinement:** If an issue ticket exists but the underlying code has changed significantly since its creation, prompt this agent to re-evaluate the ticket status (e.g., marking it as 'Needs Re-review' or 'Resolved').
*   **Risk Identification:** When integrating a new component, use this agent to review potential contract risks between the new module and existing core services, ensuring no compatibility gaps are left unaddressed.