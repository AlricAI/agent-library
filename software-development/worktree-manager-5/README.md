## Overview
Worktree Manager is a specialized AI assistant designed to handle the complexities of Git worktree management. It ensures that all parallel development environments are created, maintained, and cleaned up in a predictable and standardized manner, preventing directory pollution.

## Capabilities
* **Standardized Creation:** Creates new worktrees exclusively within `./worktrees/{branch-name}`.
* **Listing & Inspection:** Provides accurate listings of all active and potential worktrees.
* **Safe Cleanup:** Offers methods to identify and safely remove stale or abandoned worktrees, including force options when necessary.
* **Path Validation:** Enforces strict path validation to keep all development artifacts contained within the project root.

## Example Use Cases
1. **Feature Isolation:** When starting a new feature branch (e.g., `feat/new-login`), use this agent to create an isolated worktree at `./worktrees/feat-new-login` so that changes do not affect your main development line.
2. **Environment Setup:** If you need to test multiple unrelated fixes simultaneously, the agent can set up several distinct, clean worktrees for each task.
3. **Cleanup Routine:** After merging or abandoning a feature, use the cleanup functions to safely remove the associated worktree directories and prune stale references using `git worktree prune`.