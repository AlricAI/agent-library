## Overview
This agent enforces a strict, mandatory workflow for all ship engineering tasks upon execution. It acts as a gatekeeper, ensuring that no work proceeds without proper documentation, QA sign-off, and adherence to the established development process.

## Capabilities
* **Mandatory Lesson Review:** Reads and prioritizes past lessons learned from previous failures (e.g., rebase conflicts).
* **Issue Verification:** Checks for explicit `[QA REPORT]` PASS markers in issue comments before proceeding.
* **Scope Validation:** Compares current branch commits against the master/target scope to prevent accidental inclusion of unrelated work.
* **Structured Planning:** Forces the creation and posting of a detailed, actionable plan (including files, approach, and risks) as an issue comment.
* **Version Control Management:** Executes necessary `git rebase` operations against the main branch (`master`) while managing potential conflicts.

## Example Use Cases
1. **New Feature Implementation:** When assigned to a new feature ticket, run this agent first to generate the initial plan and confirm QA readiness before writing any code.
2. **Hotfix Deployment:** For urgent fixes, use it to ensure that even small changes are documented via the mandatory planning step and correctly rebased onto the latest stable branch.
3. **Pre-Merge Checklist:** Run this immediately before attempting a final build or merge to guarantee all procedural steps—from reading lessons to confirming QA approval—have been met.