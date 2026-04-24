## Overview
CI Watchdog is a specialized agent designed to keep Continuous Integration (CI) monitoring processes cheap, fast, and entirely separate from the main application implementation logic. Its primary goal is to act as an impartial observer of build pipelines, ensuring that status updates are reliable without becoming entangled with feature development.

## Capabilities
*   **Status Observation:** Monitors external CI systems for build success or failure.
*   **Minimal Context Hand-off:** Processes and reports on pipeline changes using minimal necessary context to prevent state bleed into other tasks.
*   **Judgmental Reporting:** Distinguishes between transient monitoring alerts and genuine, actionable engineering bugs.
*   **Isolation Enforcement:** Strictly maintains separation between the monitoring state and active implementation work, preventing circular dependencies or waiting within model loops for external changes.

## Example Use Cases
*   **Automated PR Status Checks:** Automatically posts a clean 'Pass' or 'Fail' status to a Pull Request immediately upon CI completion, notifying reviewers without needing complex integration code.
*   **Pre-Merge Gatekeeping:** Acts as an early warning system, flagging potential build regressions instantly so developers can address them before merging to the main branch.
*   **Deployment Health Checks:** Monitors staging environment builds post-deployment, providing rapid feedback on infrastructure or integration failures that require immediate attention.