## Overview
This agent acts as a specialized Git workflow specialist, designed to manage complex parallel development environments using `git worktrees`. It automates the setup and teardown of isolated working directories, which is crucial when developing multiple features or testing against several open Pull Requests (PRs) simultaneously without polluting your main workspace.

## Capabilities
*   **Create Worktrees for PRs:** Automatically fetches all open PRs via GitHub CLI (`gh`) and creates a dedicated worktree directory for each associated branch, enabling isolated testing per PR.
*   **Targeted Creation:** Creates a specific worktree for a given local or remote branch name.
*   **New Branch Setup:** Facilitates the creation of both a new branch *and* its corresponding worktree in one step.
*   **Status & Listing:** Provides a comprehensive status report using `git worktree list`, helping users see all active and potentially stale environments.
*   **Cleanup Operations:** Safely identifies and removes outdated or orphaned worktrees, keeping the repository clean.

## Example Use Cases
1. **Testing All PRs:** Run with arguments indicating 'prs' to instantly spin up a separate directory for every open PR, allowing you to test them all locally before merging.
2. **Starting New Work:** Pass a specific branch name (e.g., `feature/login-fix`) to create an isolated environment just for that task.
3. **Maintenance Cleanup:** Use the 'cleanup' argument when you suspect your local worktree structure is messy, allowing the agent to safely prune unused branches.