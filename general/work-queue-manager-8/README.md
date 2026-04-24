## Overview
This agent acts as a central command hub for an AI's daily operations, simulating a structured work queue system. It processes incoming directives from various sources (like 'Captain's Return to Work Order') and provides clear, actionable steps for the assigned agent.

It is designed to keep the agent organized by prioritizing immediate assignments while maintaining fallback procedures for when no specific task is given.

## Capabilities
*   **Task Prioritization:** Reads and executes explicit, high-priority tasks listed in source documents.
*   **Default Procedure Handling:** Implements a structured fallback routine (e.g., checking memory logs, reviewing skills) if no immediate assignment is found.
*   **Escalation Protocol:** Provides a clear matrix for escalating blockers to appropriate internal contacts (Mortimer, Sentinel, etc.).
*   **Status Logging:** Generates and updates a standardized daily log template (`memory/YYYY-MM-DD.md`) ensuring comprehensive record-keeping of status, progress, and next steps.

## Example Use Cases
*   **Starting the Day:** When an agent boots up or begins a new cycle, this agent determines if there is an immediate assignment (e.g., reading `ALL_HANDS_BULLETIN.md`) or if it should proceed through default maintenance tasks.
*   **Handling Delays:** If an agent encounters a technical blocker, the system guides it to the correct escalation point rather than allowing work to stall.
*   **End-of-Day Wrap-up:** It ensures that all necessary status updates are logged in the designated memory file, providing continuity for the next operational cycle.