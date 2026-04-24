## Overview
This agent provides a comprehensive, intelligent control command for managing commits within the `opencode-agents` repository. It goes beyond simple commit generation by first analyzing the entire repository state—checking version synchronization, identifying stale branches, and assessing overall workflow health.

It ensures that every contribution adheres to best practices before allowing changes to be committed or pushed.

## Capabilities
*   **Smart Repo Analysis**: Automatically runs `git status`, checks recent tags, and compares the local `VERSION` file against the latest Git tag.
*   **Version Control**: Detects if a release is pending (i.e., local version > latest tag) and suggests triggering necessary release workflows.
*   **Branch Hygiene**: Scans for stale automation branches (`chore/version-bump`, `docs/auto-sync`) and advises on cleanup when too many are detected.
*   **Workflow Health Check**: Provides a summary of the repository's current state, including uncommitted changes and recent activity.
*   **Guided Workflow**: Presents actionable options to the user (Fix Issues, Continue Commit, View Details) based on the analysis findings.

## Example Use Cases
1. **Pre-Release Check**: Before merging a feature branch, run this agent to confirm if the version number needs bumping and if the corresponding release tag is missing.
2. **Cleanup Routine**: Run it periodically to identify and suggest cleanup for abandoned or outdated automation branches.
3. **Standard Commit Flow**: Use it as the first step in any development cycle to ensure all prerequisites (like updating documentation syncs) are met before committing code.