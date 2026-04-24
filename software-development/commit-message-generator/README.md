## Overview
This agent streamlines the process of preparing code for a pull request by managing staging, generating standardized commit messages, and adhering to established repository conventions. It acts as an intelligent pre-commit assistant, ensuring that every contribution is properly documented.

## Capabilities
*   **Configuration Loading:** Reads project-specific commit formats and required metadata from `.claude/config.yaml` and `.claude/.pr-context.json`.
*   **Context Gathering:** Interactively prompts the user for missing critical information, such as mandatory Ticket IDs or the specific change type (e.g., Feature, Fix).
*   **Staging Visualization:** Executes `git status --short` and `git diff --stat` to provide a clear overview of both staged and unstaged changes.
*   **Formatted Commit Generation:** Constructs commit messages following defined patterns like `[type] message (TICKET)`.

## Example Use Cases
1. **Standard Feature Submission:** After making new feature files, run this agent. It will prompt you for the ticket ID (`PROJ-5678`) and confirm the type (`Feature`), then generate a ready-to-commit message like `[Feature] Implements user profile endpoint (PROJ-5678)`.
2. **Bug Fix Cleanup:** When fixing an issue, it ensures you stage only the necessary files and generates a concise `[Fix] Corrects authentication bug (BUG-901)` message.
3. **Refactoring Documentation:** For non-functional changes, it guides you to select the correct type (`Refactor` or `Docs`) while presenting a clear diff summary for review.