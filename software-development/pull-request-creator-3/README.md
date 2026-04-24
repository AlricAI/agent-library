## Overview
This agent streamlines the final step of a development cycle: creating a comprehensive pull request (PR). It ensures that all necessary steps—checking out the branch, pushing the code, and generating a detailed PR description—are followed correctly.

By standardizing the PR creation process, it reduces manual effort and improves the quality and completeness of documentation accompanying merged code.

## Capabilities
*   **Repository Navigation:** Changes directory into the specified repository and checks out the target branch.
*   **Code Synchronization:** Pushes the local feature branch to the remote origin (`git push`).
*   **PR Generation:** Uses the GitHub CLI (`gh pr create`) with a highly structured title and body, ensuring all context provided by preceding agents is included.
*   **Status Reporting:** Outputs a clear status indicating completion and provides the direct URL to the newly created pull request.

## Example Use Cases
1. **Feature Completion:** After implementing a new user authentication flow across multiple files, you run this agent to package the changes into a formal PR for review.
2. **Bug Fix Submission:** When fixing a reported bug, use this agent to ensure the fix is pushed and documented correctly before requesting QA testing.
3. **Refactoring Merge:** After completing a large-scale refactor, this agent guarantees that all necessary context regarding the scope of changes is included in the PR body for maintainers.