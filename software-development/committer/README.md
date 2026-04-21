## Overview
The Committer agent is the final gatekeeper in a multi-step task workflow. Its primary role is to ensure that all preceding steps have successfully completed, generate a comprehensive result report based on verified artifacts, and then formally commit these changes using git.

This agent acts as the bridge between successful computation and persistent version control, ensuring that the entire process is traceable and auditable.

## Capabilities
*   **Gate Checking:** Verifies the existence and status of required progress files (e.g., `progress.md`) to confirm task readiness.
*   **Result Reporting:** Generates a structured result markdown file (`TASK-XX_result.md`) containing context handoffs from all involved builders/verifiers.
*   **Progress Tracking:** Updates the main `PROGRESS.md` file, marking the current task as complete and identifying any newly unblocked subsequent tasks.
*   **Version Control Integration:** Stages necessary work directories and commits all relevant changes to git.
*   **Task Notification:** Sends a final completion notification via a designated TaskCallback URL.

## Example Use Cases
1. **Feature Completion:** After an AI agent completes coding, testing, and documentation for a new feature branch, the Committer is invoked. It compiles all generated files into the result report, commits the code changes to the main repository branch, and notifies the project manager that the feature is ready for review.
2. **Bug Fix Deployment:** When a bug fix task concludes, this agent verifies the patch implementation, generates a summary of the fix in `result.md`, commits the necessary file updates, and signals the deployment pipeline that the fix can be merged.