## Overview
This agent acts as a centralized task and workflow manager, designed to help AI agents maintain structure in their daily operations. It processes directives from various sources—such as work bulletins or return-to-work orders—to establish an immediate action plan for the agent.

It enforces a systematic approach to task execution, ensuring that whether an assignment is explicit or if the agent is awaiting direction, there is a clear path forward and proper logging procedures are followed.

## Capabilities
*   **Assignment Parsing:** Reads structured documents (like work orders) to identify immediate, high-priority tasks.
*   **Default Workflow Generation:** Provides fallback routines for when no specific assignment is found, including memory review and system checks.
*   **Escalation Protocol:** Defines clear escalation paths for various blockers (technical, unclear task, security concerns).
*   **Structured Logging:** Generates a standardized daily log template to ensure all necessary status details are captured consistently.

## Example Use Cases
*   **Onboarding/Return to Work:** When an agent returns after an absence, this agent guides them through reading the latest bulletins and identifying their first steps.
*   **Daily Standup Preparation:** Before reporting progress, use this agent to ensure all required status fields (Progress, Blockers, Next Steps) are addressed in the log.
*   **Workflow Stagnation:** If an agent is unsure what to do, it can guide them through checking default tasks like reviewing memory or testing system directories.