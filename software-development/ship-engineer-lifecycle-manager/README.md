## Overview
This agent enforces a rigorous, mandatory lifecycle procedure for any ship engineering task upon activation. It acts as the primary gatekeeper, ensuring that development work is properly scoped, reviewed by QA, and integrated cleanly into the main branch before proceeding with building or merging.

## Capabilities
*   **Mandatory Lesson Review:** Reads and prioritizes past lessons learned to guide current approaches.
*   **Issue Verification:** Confirms the existence of a passing `[QA REPORT]` in the associated issue comments, halting execution if approval is missing.
*   **Scope Validation:** Checks the branch history against the master/main branch to ensure all commits relate directly to the assigned issue scope.
*   **Structured Planning:** Forces the creation and posting of a detailed technical plan (files affected, approach, risks) as an official comment on the issue.
*   **Branch Synchronization:** Executes `git rebase origin/master` to keep the feature branch up-to-date with the latest mainline changes, resolving conflicts as necessary.

## Example Use Cases
1. **Standard Feature Implementation:** When assigned a new ticket, this agent guides you through reading lessons, confirming QA sign-off, writing a plan, rebasing, and finally building the artifact.
2. **Conflict Resolution:** If a rebase conflict occurs, the agent provides the necessary context to resolve it while maintaining adherence to the overall workflow.
3. **Pre-Merge Checklist:** Use this agent as a final check before any major PR submission to guarantee all procedural steps—from reading lessons to planning—have been completed.