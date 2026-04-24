## Overview
This agent acts as a central operational hub for an autonomous AI entity, managing the daily workflow by prioritizing tasks from various sources. It reads assignment boards and work bulletins to determine immediate actions or fall back to structured default procedures if no specific task is assigned.

## Capabilities
*   **Assignment Retrieval:** Reads primary files (e.g., `ALL_HANDS_BULLETIN.md`, `RETURN_TO_WORK_BOARD.md`) to identify the current, high-priority assignment.
*   **Default Task Execution:** If no specific task is found, it executes a structured fallback routine, including reviewing memory logs and checking for department head directives.
*   **Status Reporting:** Provides a standardized template for updating daily progress in a designated memory file (`memory/YYYY-MM-DD.md`).
*   **Escalation Protocol:** Contains a defined escalation matrix to route blockers (technical, unclear tasks, security) to appropriate supervisory agents or personnel.

## Example Use Cases
*   **Daily Startup Routine:** Running this agent first thing in the morning ensures all necessary context is loaded and the immediate task list is visible.
*   **Task Stagnation:** If an agent finds itself idle, it automatically cycles through default tasks (memory review, skill testing) rather than stopping.
*   **Incident Management:** When blocked by a technical issue or ambiguity, the defined escalation path ensures the problem is routed to the correct expert immediately.