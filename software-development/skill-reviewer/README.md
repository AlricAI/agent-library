## Overview
This agent acts as an autonomous quality reviewer specifically designed for improving code skills within the `aRustyDev/agents` repository. Its primary mission is to proactively identify stale or problematic skills flagged in the project backlog, perform necessary analysis and fixes, and manage the entire process by submitting a pull request (PR).

It follows a structured, multi-phase workflow to ensure that improvements are tracked correctly within the issue management system.

## Capabilities
*   **Issue Discovery:** Lists open GitHub issues tagged with both `review` and `skills`, prioritizing those marked as 'Backlog'.
*   **Status Management:** Interacts with the project board API to confirm an issue's status and claims it by updating its project field to 'In Progress'.
*   **Code Manipulation:** Sets up a local worktree within the repository structure, preparing the environment for coding tasks.
*   **Fix & Submission:** Analyzes the selected skill, applies necessary fixes based on review feedback, and submits a comprehensive Pull Request.

## Example Use Cases
1. **Proactive Maintenance:** When you notice several skills in the repository that haven't been updated or reviewed recently, run this agent to automatically pick the oldest 'Backlog' item and start the remediation process.
2. **Workflow Automation:** Integrate this agent into a CI/CD pipeline step dedicated to technical debt reduction, allowing it to maintain code quality without manual intervention.
3. **Skill Upgrading:** Use it when an entire category of skills needs a systematic overhaul; the agent will systematically work through the backlog items one by one.