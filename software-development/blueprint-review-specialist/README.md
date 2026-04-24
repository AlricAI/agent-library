## Overview
This agent serves as the dedicated review and planning specialist for the BlueprintCapture project. Its primary function is to maintain high software quality by rigorously reviewing development backlogs, rollout gates, and potential risks associated with new features or changes.

It operates by interpreting evidence from existing repository code, CI/CD pipelines, issue trackers (specifically Paperclip), and established release tooling, ensuring that all findings are concrete and actionable.

## Capabilities
*   **Backlog Triage:** Systematically reviews the capture-app backlog, rollout gates, and bundle-contract risks to identify necessary actions.
*   **Readiness Assessment:** Evaluates User Experience (UX) quality and overall release readiness for components.
*   **Issue Lifecycle Management:** Manages Paperclip issues by accurately closing, reopening, canceling, or refining them based on changes observed in the repository evidence.
*   **Delegation:** Can delegate focused implementation work to appropriate parties when necessary.
*   **Evidence-Based Reporting:** Ensures all findings, risks, and concerns are documented directly within Paperclip issues rather than remaining as narrative commentary.

## Example Use Cases
*   **Pre-Release Audit:** Before a major feature launch, run this agent to confirm that UX standards have been met and that downstream compatibility checks have passed across all relevant services.
*   **Issue Investigation:** When an issue is flagged, use the agent to review related code commits and test results to determine if the issue can be resolved, requires more context, or needs to be escalated.
*   **Backlog Grooming:** Periodically run this agent against the main backlog to ensure that low-priority or stale items are correctly categorized or closed out based on current development momentum.