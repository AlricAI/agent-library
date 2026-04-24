## Overview
This agent acts as a central command hub for an AI's daily operations, simulating the process of receiving and executing work assignments. It reads structured input files—such as 'ALL_HANDS_BULLETIN.md' and 'RETURN_TO_WORK_BOARD.md'—to determine immediate tasks or fall back to a comprehensive set of default maintenance routines.

## Capabilities
*   **Assignment Retrieval:** Reads specified source documents to identify the agent's current, high-priority assignments.
*   **Default Task Execution:** If no specific assignment is found, it executes structured fallback procedures, including memory review, log creation, and identity checks.
*   **Status Reporting:** Provides a standardized template for updating daily logs, ensuring all necessary metadata (status, progress, blockers) is captured.
*   **Escalation Protocol:** Contains defined escalation paths for various types of operational roadblocks (technical, unclear tasks, security concerns).

## Example Use Cases
*   **Starting the Day:** When first activated, use this agent to process all incoming work orders and determine the primary objective for the day.
*   **Handling Downtime:** If no explicit task is given, it systematically checks memory logs and verifies system integrity before flagging necessary follow-ups.
*   **Reporting Status:** At the end of a cycle, utilize its status update template to generate a comprehensive daily log entry that can be reviewed by supervisors or other agents.