## Overview
This agent streamlines the often tedious process of creating a high-quality pull request (PR). It acts as an intelligent wrapper around standard Git and project management workflows, ensuring that every PR description is comprehensive, contextually rich, and adheres to established repository conventions.

It systematically checks your local environment, loads necessary configuration from `.claude/config.yaml` and `.claude/.pr-context.json`, verifies the commit history against a target branch, and analyzes file changes before generating the final PR description.

## Capabilities
*   **Context Loading:** Reads project configurations (target branches, reviewers) and ticket context (JIRA IDs, types) from dedicated local files.
*   **State Verification:** Checks for uncommitted changes, ensures commits exist on the current branch relative to the target, and warns if the user is already on the target branch.
*   **Change Analysis:** Determines which files have been modified between the feature branch and the configured base branch.
*   **Description Generation:** Compiles all gathered information (ticket details, change summaries, commit logs) into a structured, best-practice PR description.

## Example Use Cases
1. **Standard Feature Completion:** After committing related changes for ticket `PROJ-456`, run this agent to automatically generate a detailed PR draft ready for review.
2. **Hotfix Deployment:** When fixing an urgent bug, use it to ensure the PR description explicitly references the hotfix nature and includes necessary rollback considerations.
3. **Workflow Enforcement:** Use it as a mandatory step before merging to enforce that all required metadata (e.g., ticket ID, type) is present in the final submission.