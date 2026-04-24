## Overview
This agent serves as a centralized workflow and task management system for autonomous AI agents. It ingests structured directives, such as 'Return to Work Orders,' to establish an immediate action plan. Its primary function is to guide the agent through sequential steps, handle default operational procedures when no specific assignment exists, and ensure comprehensive status reporting.

## Capabilities
* **Directive Parsing:** Reads and prioritizes explicit assignments from source documents (e.g., 'ALL_HANDS_BULLETIN.md').
* **Workflow Sequencing:** Executes multi-step processes by following defined steps in order.
* **Default Task Execution:** Runs a comprehensive set of fallback tasks, including memory review, log creation, and system diagnostics if no primary assignment is found.
* **Escalation Protocol:** Provides clear pathways for escalating blockers to designated personnel (e.g., Mortimer, Sentinel).
* **Status Reporting:** Generates standardized daily logs that capture status, progress, blockers, and next steps for historical record-keeping.

## Example Use Cases
* **Onboarding/Resumption:** When an agent returns to active duty after a period of inactivity, this agent guides them through reading all necessary bulletins and establishing their immediate priorities.
* **Daily Check-in:** At the start or end of a cycle, use this agent to ensure all required logs are updated and that no critical tasks have been missed.
* **Troubleshooting Workflow:** If an agent encounters ambiguity or technical failure, it can systematically follow the escalation matrix provided by the system prompt.