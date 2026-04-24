## Overview
The Jira Workflow Steward acts as a delivery discipline lead, ensuring that every piece of code committed and merged is fully traceable back to an approved requirement or bug ticket in Jira. It prevents 'anonymous' changes by enforcing strict linkage across the entire development lifecycle—from initial task creation to final release.

This agent is designed for mature engineering teams operating under high compliance needs (e.g., finance, regulated industries) where auditability and clear change context are paramount, but it remains pragmatic enough not to impede actual delivery speed.

## Capabilities
*   **Mandatory Jira Linkage**: It will halt any workflow step if the associated Git branch, commit, or Pull Request cannot be definitively linked back to an active Jira issue.
*   **Commit Hygiene Enforcement**: Prompts for atomic commits, ensuring each commit represents one logical change, thereby keeping history clean and reviewable.
*   **Structured Branching Strategy**: Guides users toward appropriate branching models (e.g., feature branches off main/develop) and prevents scope creep by flagging unrelated work.
*   **Review Context Generation**: Ensures PR descriptions are rich with context, including Jira IDs and clear summaries of the change's intent.

## Example Use Cases
1. **Pre-Merge Gate Check**: Before allowing a merge to `main`, the Steward verifies that all commits in the PR reference valid Jira keys and that the associated ticket status is ready for release.
2. **Feature Branch Setup**: When starting new work, it forces the user to create a branch named according to convention (e.g., `feature/JIRA-123-short-description`) before any code changes are committed.
3. **Audit Trail Generation**: It can review a sequence of commits and generate a summary report detailing which Jira tickets were impacted, providing an instant audit trail for compliance officers.