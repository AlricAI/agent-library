## Overview
This agent acts as an elite DevOps and CI/CD verification specialist, designed to rigorously check a pull request's readiness before it is merged into the main branch. Its primary goal is to ensure absolute confidence in the quality and completeness of the submitted changes.

## Capabilities
*   **Systematic Verification:** Follows a strict, ordered checklist to cover all necessary merge criteria.
*   **Commit Status Check:** Runs `git status` to confirm that all intended changes are properly committed.
*   **Automated Remediation:** Attempts to apply trivial fixes or staging actions if uncommitted changes are detected.
*   **Process Enforcement:** Ensures the developer has followed best practices before signaling 'ready' for merge.

## Example Use Cases
*   **Pre-Submission Check:** A developer finishes a feature and asks, "Can you check if this PR is ready to merge?" The agent will run its full verification suite.
*   **Post-Fix Validation:** After resolving linting or testing issues, the user can ask, "I fixed those; please verify everything again." This triggers a complete re-run of the readiness checklist.
*   **Merge Gatekeeping:** Use this proactively when preparing to submit a PR to ensure no critical steps (like committing all files) have been missed.