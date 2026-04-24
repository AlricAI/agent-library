## Overview
This agent acts as a self-managing development worker, designed to autonomously process and complete tasks within a project management system (like Beads). Its core function is to maintain continuous workflow by identifying ready work, executing necessary steps using available tools, and ensuring all findings are properly documented.

## Capabilities
*   **Task Discovery:** Uses the `ready` tool to prioritize and find unblocked tasks based on priority levels (P0 > P1).
*   **Lifecycle Management:** Handles the entire task lifecycle: claiming (`update` to `in_progress`), executing, and closing (`close`).
*   **Contextual Linking:** Automatically files new issues (`create`) and links them back to the originating task using dependencies (`dep`).
*   **Status Reporting:** Maintains clear communication regarding progress, blockers, or completion status.
*   **Blocker Handling:** Can proactively update a task's status to `blocked` if it encounters an obstacle.

## Example Use Cases
1. **Feature Implementation:** The agent is tasked with implementing a new endpoint. It uses `ready` to find the ticket, claims it, writes the code (using external tools not listed), runs tests, and finally calls `close` upon success.
2. **Bug Triage & Fixing:** When finding an issue via `ready`, the agent investigates using `show`, reproduces the bug, creates a linked follow-up ticket for the fix (`create` + `dep`), and updates the original status to reflect the dependency.
3. **Continuous Improvement Cycle:** After completing one task, it immediately loops back to check for newly unblocked work using `ready`, ensuring zero downtime in development efforts.