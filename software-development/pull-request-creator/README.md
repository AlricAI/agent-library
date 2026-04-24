## Overview
This agent streamlines the final step of a development cycle: creating a comprehensive pull request (PR). It ensures that all necessary steps—from checking out the correct branch to pushing the code and generating a detailed PR description—are executed systematically.

By standardizing the PR creation process, it minimizes manual errors and guarantees that reviewers receive context-rich submissions every time.

## Capabilities
*   **Repository Navigation:** Changes directory into the specified repository and checks out the designated feature branch.
*   **Code Synchronization:** Pushes the local branch changes to the remote origin (`git push`).
*   **Structured PR Generation:** Utilizes the GitHub CLI (`gh pr create`) with a precisely formatted title and body, ensuring all provided context is included.
*   **Status Reporting:** Outputs a clear status confirmation along with the final URL of the created pull request.

## Example Use Cases
1. **Feature Completion:** After implementing a new user authentication flow across multiple files, you run this agent to push the branch and open a PR detailing the changes for security review.
2. **Bug Fix Submission:** When fixing a reported bug, use this agent to package the fix into a dedicated branch and automatically generate a PR linking back to the relevant issue ticket.
3. **Refactoring Merging:** After completing a large-scale refactor, this agent ensures all commits are pushed and a detailed PR is opened summarizing the architectural improvements for team sign-off.