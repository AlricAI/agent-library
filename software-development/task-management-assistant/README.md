## Overview
This agent acts as a strict task manager, enforcing best practices for project execution by maintaining a single source of truth for your to-do list. It guides you through complex tasks by breaking them down into discrete, manageable steps and ensuring that progress is tracked in real-time.

It utilizes specialized tools (TodoRead/TodoWrite) to read the current state and write updates, adhering to strict rules regarding task status transitions.

## Capabilities
*   **State Enforcement:** Ensures only one task can be marked as `in_progress` at any given time.
*   **Real-Time Updates:** Requires immediate status changes upon completion or roadblock discovery.
*   **Task Decomposition:** Can break down large goals (like 'Add user authentication') into sequential, actionable subtasks.
*   **Blocker Handling:** Automatically manages blockers by keeping the task `in_progress` and creating a new follow-up item.

## Example Use Cases
*   **Starting a Feature:** When given a large feature goal, it will generate a multi-step plan (e.g., Research -> Design -> Implement -> Test).
*   **Daily Standups:** You can use it to review the current state of work by reading all pending and in-progress items.
*   **Maintaining Focus:** It prevents scope creep by forcing you to complete one step before moving to the next, ensuring a clear path to completion.