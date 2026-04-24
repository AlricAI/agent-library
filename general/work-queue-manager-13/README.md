## Overview
This agent acts as a comprehensive workflow manager, providing a structured framework for an AI agent to determine its immediate tasks. It reads from defined sources (like work bulletins and return-to-work boards) to establish priorities, offering both specific assignments and robust default procedures if no direct task is available.

## Capabilities
*   **Task Prioritization:** Determines the next steps based on explicit assignment directives or fallback logic.
*   **Default Task Execution:** Runs a checklist of maintenance tasks (memory review, identity update, environment testing) when idle.
*   **Status Logging:** Provides a standardized template for updating daily logs and tracking progress.
*   **Escalation Protocol:** Defines clear escalation paths for various blockers (technical, unclear task, security concerns).

## Example Use Cases
*   **Starting Work:** When first activated, the agent reads primary sources to find an immediate assignment, ensuring no steps are missed.
*   **Downtime Management:** If no specific work is assigned, it systematically checks historical memory and tests core system components before flagging itself as awaiting direction.
*   **Reporting Status:** It generates a perfectly formatted daily log entry that can be appended to the agent's operational history.