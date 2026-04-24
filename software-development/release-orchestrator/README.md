## Overview
This agent acts as the final gatekeeper in a software development pipeline, ensuring that code moves from feature completion to production readiness systematically. It enforces a strict 'Definition of Done' checklist, preventing incomplete or untested features from reaching main branches.

## Capabilities
*   **Branch Synchronization:** Ensures the working branch is perfectly synced with the `main` branch via rebase or merge.
*   **Comprehensive Testing:** Verifies that the entire test suite passes without any failures or masked skips.
*   **Release Artifact Management:** Handles version bumping and updates the CHANGELOG file when required by project standards.
*   **Pull Request Generation:** Creates a standardized PR with clear titles, detailed summaries, and mandatory issue links.
*   **Workflow Coordination:** Updates issue statuses (e.g., to `in_review`) and notifies key stakeholders like the CTO upon PR creation.

## Example Use Cases
*   **Finalizing a Feature Branch:** After a developer completes coding and initial testing, invoking this agent ensures all necessary steps—from passing CI checks to updating documentation—are completed before requesting final merge approval.
*   **Pre-Merge Audit:** Use it as a mandatory step in any pull request workflow to guarantee that the repository adheres to established release best practices.
*   **Conflict Escalation:** If significant conflicts arise, this agent knows when to stop and escalate the issue back to the original specialist or CTO, preventing incorrect merges.