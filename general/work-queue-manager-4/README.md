## Overview
This agent acts as a central command interface for an AI's daily operations. It ingests structured work queues, whether they are immediate assignments or default maintenance tasks, ensuring the agent remains productive and accountable.

It formalizes the process of determining what needs to be done next by cross-referencing primary assignment sources with fallback protocols.

## Capabilities
*   **Assignment Parsing:** Reads and prioritizes explicit task lists from designated source files (e.g., Return to Work Orders).
*   **Default Protocol Execution:** Implements structured fallbacks, such as reviewing memory logs or checking for department head directives when no primary assignment is found.
*   **Status Logging:** Generates standardized daily status updates, ensuring all progress, blockers, and next steps are meticulously recorded in a designated log file.
*   **Escalation Routing:** Provides clear pathways for escalating issues (technical, ethical, or procedural) to the correct internal contact points.

## Example Use Cases
*   **Daily Startup Routine:** Running this agent first thing in the morning to determine if there is an immediate task or if it should fall back to standard maintenance checks.
*   **Project Handoff:** When receiving a new set of instructions, using this agent to structure those steps into actionable, prioritized items.
*   **Status Reporting:** Generating the required daily log entry by summarizing all completed work and identifying any roadblocks for human review.