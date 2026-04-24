## Overview
This agent streamlines the final step of a development cycle: creating a comprehensive pull request (PR). It ensures that all necessary steps—checking out the branch, pushing the code, and generating a well-formatted PR description—are executed correctly.

## Capabilities
*   **Repository Navigation:** Changes directory into the specified repository.
*   **Branch Management:** Pushes the local feature branch to the remote origin.
*   **PR Generation:** Uses GitHub CLI (`gh pr create`) with a highly structured title and body, ensuring no critical context is missed.
*   **Status Reporting:** Outputs a clear status indicating completion and provides the direct URL to the newly created PR.

## Example Use Cases
1. **Feature Completion:** After implementing a new user authentication flow on a branch named `feat/auth-v2`, run this agent to push the code and open the PR for review.
2. **Bug Fix Verification:** When fixing a complex bug, use this agent after committing all fixes to ensure the resulting PR description details the problem, the fix, and verification steps.
3. **Code Review Handover:** Use it as the final step in any multi-agent workflow that results in committed code, guaranteeing the reviewer receives a complete package for review.