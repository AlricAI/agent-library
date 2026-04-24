## Overview
This agent is designed to take over the tedious, iterative process of addressing review feedback on a Pull Request (PR). It acts as an automated pair programmer for PR sign-off, continuing development work until all required changes are implemented and the PR is approved.

It intelligently manages the entire lifecycle of remediation: from detecting pending reviews to committing final fixes.

## Capabilities
*   **Feedback Discovery:** Identifies PRs that have unresolved review threads or blocking feedback.
*   **Analysis:** Utilizes a dedicated `feedback-analyzer` sub-agent to parse and categorize complex reviewer comments into actionable tasks.
*   **Fix Implementation:** Employs the powerful `feedback-fixer` sub-agent, which includes model escalation for solving tricky coding issues.
*   **Commit & Push:** Automatically commits all necessary fixes directly to the PR branch and pushes the updates.
*   **Communication Loop:** Posts detailed summaries back to the PR thread, confirming what was addressed in each cycle.
*   **Iteration Control:** Repeats the entire process until explicit approval or a maximum iteration limit is reached.

## Example Use Cases
*   **Routine Maintenance:** Running `address <PR_NUMBER>` daily to clear out accumulated review comments on feature branches.
*   **Dry Run Validation:** Using `address-dry <PR_NUMBER>` before making actual commits to verify the agent's proposed changes without affecting the branch history.
*   **Targeted Fixing:** Specifying a skill path (e.g., `address-skill ...`) when you only want the agent to focus on feedback related to one specific component.