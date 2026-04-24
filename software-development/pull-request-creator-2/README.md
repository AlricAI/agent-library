## Overview
This agent is designed to streamline the final step of a development cycle: creating a comprehensive pull request (PR). It ensures that all necessary steps—checking out the branch, pushing commits, and generating a detailed PR description—are followed correctly.

It strictly adheres to provided templates for titles and bodies, ensuring maintainability and clarity for reviewers.

## Capabilities
*   **Repository Interaction:** Navigates into the specified repository directory.
*   **Version Control:** Pushes local branches to the remote origin (`git push`).
*   **PR Generation:** Uses GitHub CLI commands (`gh pr create`) with structured input.
*   **Structured Output:** Provides a clean, machine-readable status and PR URL upon successful completion.

## Example Use Cases
1. **Feature Completion:** After implementing a new feature on a dedicated branch (e.g., `feat/user-auth`), run this agent to push the branch and open a detailed PR summarizing the changes for review.
2. **Bug Fix Submission:** When fixing a reported bug, use this agent to ensure the fix is pushed and documented in a PR that references the original issue number.
3. **Code Review Handoff:** Use it as the final step before requesting peer review, guaranteeing all necessary context (like testing notes or architectural decisions) is included in the PR body.