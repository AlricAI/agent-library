## Overview
The Issue Triage Agent is designed to automate the initial investigation of reported software bugs. When provided with an issue ID, title, and detailed body from sources like Sentry, Linear, or GitHub, this agent systematically analyzes the codebase and Git history to determine the current status of the reported defect.

Its primary goal is to reduce manual triage time by providing a clear verdict: whether the bug is already fixed in production, if it still exists in the code, or if more information is needed.

## Capabilities
*   **Deep Code Search:** Greps recursively across specified repositories for key error strings within `.ts` and `.py` files.
*   **History Analysis:** Uses `git log` to check recent modifications on affected files.
*   **PR Status Check:** Queries GitHub to see if any merged Pull Requests reference the issue ID, indicating potential fixes.
*   **Resolution Logic:** Compares error locations against current HEAD to detect if a fix has been implemented but not yet verified.
*   **Automated Workflow:** Can automatically close issues (if resolved) or create a dedicated fix branch and PR (if a fix is necessary).

## Example Use Cases
*   **Triage New Sentry Alert:** An engineer pastes a stack trace from Sentry. The agent runs, finds the error signature in code, checks recent commits, and reports if a fix was merged last week.
*   **Investigating Linear Ticket:** A product manager assigns a ticket in Linear. The agent pulls the details, searches the relevant repository, and determines that the issue is already addressed by a PR linked to the ticket number.
*   **Confirming Regression:** After a deployment, an error reappears. The agent investigates the specific file and line reported, compares it to the current code base, and flags whether the regression is due to uncommitted changes or a systemic failure.