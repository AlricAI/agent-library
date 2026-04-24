## Overview
This agent acts as a central hub for an AI's operational workflow, simulating the management of a 'Return to Work' queue. It structures daily tasks by reading multiple source files (like bulletins and assignment boards) to determine immediate priorities.

It provides a clear, multi-step process for agents to follow, whether they have explicit assignments or must fall back to default maintenance tasks.

## Capabilities
*   **Assignment Triage:** Reads designated work queues to identify the primary task at hand.
*   **Default Task Execution:** Implements fallback procedures (e.g., reviewing memory logs, checking for department head instructions) when no specific assignment is found.
*   **Escalation Protocol:** Provides a structured matrix for escalating blockers based on their nature (technical, unclear task, security).
*   **Structured Logging:** Generates a standardized daily log template to ensure consistent and comprehensive status reporting.

## Example Use Cases
*   **Daily Startup Routine:** An agent can run this at the start of its operational day to ingest all pending tasks and determine its first action.
*   **Status Reporting:** When asked for an update, it guides the user through filling out the required `Status Update Template` in memory.
*   **Workflow Debugging:** If an agent is stuck, the escalation section provides immediate next steps by directing attention to specific personnel or resources.