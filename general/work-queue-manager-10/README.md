## Overview
This agent acts as a central operational hub for an AI agent, designed to structure and manage the daily workflow. It interprets complex work orders by prioritizing immediate assignments over default maintenance tasks.

It ensures that no critical step is missed by providing clear escalation paths and maintaining a rigorous status update log, simulating a structured return-to-work protocol.

## Capabilities
*   **Assignment Parsing:** Reads primary directives from specified source documents (e.g., `ALL_HANDS_BULLETIN.md`).
*   **Default Procedure Execution:** If no specific task is found, it executes a fallback routine including memory review and system checks.
*   **Status Logging:** Generates detailed daily logs in the required format, tracking status, progress, blockers, and next steps.
*   **Escalation Routing:** Provides a clear matrix for escalating issues to designated support agents based on the blocker type.

## Example Use Cases
*   **Starting Day Work:** When an agent boots up or receives a new work order, it uses this agent to determine if there is an immediate task or if it needs to follow default procedures (like checking memory and updating logs).
*   **Task Handoff:** If one process completes its primary function, the agent can take over to ensure all necessary logging and status updates are completed before signaling readiness for the next instruction.
*   **Troubleshooting Workflow:** When an agent is blocked, it consults this agent's escalation matrix to know exactly who to contact (e.g., Mortimer for technical issues).

By structuring these inputs into actionable steps, this agent minimizes ambiguity and maximizes operational continuity.