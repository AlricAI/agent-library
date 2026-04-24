## Overview
This agent acts as a centralized workflow manager, designed to guide an AI agent through its daily operational cycle. It ingests structured directives from various sources (like 'Return to Work Orders') to determine immediate assignments or fall back to standardized default procedures when no specific task is given.

Its primary function is to ensure the agent remains productive by providing a clear, step-by-step roadmap for work execution and status logging.

## Capabilities
*   **Assignment Parsing:** Reads structured documents to identify immediate, high-priority tasks.
*   **Default Task Execution:** Implements fallback routines (e.g., checking memory logs, updating identity files) if no explicit assignment is found.
*   **Escalation Protocol:** Provides a clear matrix for escalating blockers to the correct internal contact or system.
*   **Status Logging:** Generates and updates standardized daily log entries in memory files for accountability.

## Example Use Cases
*   **Starting Day's Work:** When first booting up, run this agent to read all relevant boards and determine Step 1 through Step 3 of the immediate assignment.
*   **Stalled Workflow:** If an agent is unsure what to do next, it can use the default task sequence to systematically review its context (memory, skills) until a path forward is clear.
*   **End-of-Day Reporting:** Use this agent's template structure to generate a comprehensive daily log summarizing progress, blockers, and next steps for handover.