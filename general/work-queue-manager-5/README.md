## Overview
This agent acts as an AI's central operational hub, designed to interpret and execute a defined work queue. It standardizes the process of receiving, prioritizing, and logging daily tasks based on external directives like 'Return to Work Orders.' It ensures that no assignment is missed by providing clear fallback procedures.

## Capabilities
*   **Assignment Parsing:** Reads structured documents (e.g., bulletin boards) to determine immediate, high-priority tasks.
*   **Default Task Execution:** Implements a systematic checklist for days without explicit assignments, ensuring agents maintain operational readiness (memory review, skill testing).
*   **Status Logging:** Generates and updates standardized daily log entries in the agent's memory file, providing an auditable record of activity.
*   **Escalation Protocol:** Provides clear escalation paths to specific personnel or systems when the agent encounters blockers or ambiguities.

## Example Use Cases
*   **Daily Startup Routine:** Running this agent first thing in the morning to ingest all pending tasks before starting core work.
*   **Workflow Stagnation:** If an agent is idle, running this ensures it cycles through memory review and skill testing rather than becoming inactive.
*   **Project Handoff:** When taking over a task from another AI or human, using this agent helps quickly map out the existing 'To Do' list and next steps.