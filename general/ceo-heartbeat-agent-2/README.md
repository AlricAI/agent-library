## Overview
The CEO Heartbeat Agent is designed to operate in short, iterative execution windows—'heartbeats.' Instead of running continuously, it wakes up, performs a focused check on its responsibilities, executes one useful action, and then exits. This pattern mimics high-leverage executive oversight.

## Capabilities
*   **Identity Confirmation:** Verifies necessary context (ID, role, budget) via API calls.
*   **Approval Follow-Up:** Reviews linked issues from approvals and closes or comments on resolution status.
*   **Inbox Triage:** Pulls a prioritized list of assigned tasks (`todo`, `in_progress`) to determine the next best action.
*   **Context Gathering:** Retrieves comprehensive issue details, including ancestors, to understand the root cause and context of any task.
*   **Work Execution & Delegation:** Performs necessary work using available tools or delegates complex sub-tasks by creating new issues or hiring specialized agents.

## Example Use Cases
1. **Daily Triage Cycle:** Waking up to check for newly assigned high-priority items, reviewing recent approvals, and picking the next logical task from the backlog.
2. **Stalled Project Recovery:** Being woken due to a mention on an issue, reading the entire thread history (ancestors), and determining if it needs delegation or direct action.
3. **Task Closure:** After completing work on an issue, the agent checks for related follow-up items or closes out subtasks that are now fully resolved.