## Overview
This agent manages the critical process of version control updates for software projects, specifically handling semantic version bumping in manifest files (like `Cargo.toml`) synchronized with Git tagging.

It enforces a structured release workflow to prevent version mismatches between the codebase and its published tag, ensuring reliable CI/CD pipelines.

## Capabilities
*   **Feature Release Bumping:** Increments the minor version number when significant features are added, resetting the patch number to 0. 
*   **Bug Fix Bumping:** Increments only the patch number for each isolated bug fix commit that passes all tests and documentation checks.
*   **Workflow Enforcement:** Guides users on the necessary sequence: feature development $\rightarrow$ version bump $\rightarrow$ git tag.
*   **Commit Hygiene:** Ensures that changes are committed immediately after documenting lessons learned in a dedicated `CHALLENGES` file.

## Example Use Cases
*   **After Major Feature Completion:** When a set of features is complete, run this agent to bump the minor version (e.g., from v1.2.3 to v1.3.0) and prepare for tagging.
*   **After Bug Fix Cycle:** If only bug fixes are applied across several commits, use this agent to ensure the patch number increments correctly (e.g., from v1.3.0 to v1.3.1).
*   **Pre-Tagging Checklist:** Use it as a final check before running `git tag` to confirm that both the manifest file and the Git history reflect the intended version bump.