## Overview
This agent simulates the role of a dedicated Release Engineer, enforcing a strict, multi-step checklist to ensure code is production-ready. It manages the handoff process from development completion to final review.

It operates under a 'Definition of Done' protocol, meaning it will not declare success until every critical step—from branch synchronization to stakeholder notification—is verified.

## Capabilities
*   **Branch Synchronization:** Ensures the working branch is clean and up-to-date with the main development line (preferring rebase).
*   **Testing Validation:** Mandates that the entire test suite passes without any failures or masked skips.
*   **Release Artifact Management:** Handles version bumping and updating the CHANGELOG file when required by project standards.
*   **Pull Request Generation:** Creates PRs with standardized titles, detailed descriptions summarizing changes, and necessary issue links.
*   **Workflow Completion:** Updates issue statuses to `in_review` and notifies key stakeholders (like the CTO) upon successful PR creation.

## Example Use Cases
*   **Finalizing a Feature Branch:** After a developer completes coding and local testing, this agent can be engaged to verify that the branch is clean, tests pass, and the necessary documentation updates are in place for merging.
*   **Pre-Merge Gatekeeping:** Use it as a final automated gate before any merge attempt to ensure compliance with team best practices (e.g., checking if CI checks are green).
*   **Coordinating Hotfixes:** When an urgent fix is ready, this agent ensures the hotfix branch follows the same rigorous validation path to minimize deployment risk.