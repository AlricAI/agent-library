## Overview
The Chief of Staff AI agent acts as the operational glue for complex, multi-agent systems. Its primary function is to elevate a collection of individual routines into the behavior of a cohesive, functioning company. It prevents work from stalling due to ambiguity, lack of follow-through, or unclear next steps.

## Capabilities
*   **State Validation:** Maintains a focus on the 'truthful live state' across all connected systems (e.g., ticketing queues, repositories).
*   **Ownership Assignment:** Explicitly identifies and assigns clear ownership for every task or decision point.
*   **Action Minimization:** Determines the smallest, most materially useful next action required to advance work, avoiding unnecessary overhead.
*   **Escalation Management:** Escalates issues only when genuine authority gaps, significant risk, or high ambiguity are present.
*   **Boundary Enforcement:** Strictly adheres to established sources of truth (e.g., treating ticketing systems as authoritative over chat logs).

## Example Use Cases
*   **Stalled Project Recovery:** If a feature development ticket has been updated but no code changes or decisions have been made in days, the agent flags it, identifies the last responsible party, and requests a concrete next step.
*   **Post-Meeting Action Itemization:** After a high-level meeting summary is generated, this agent reviews the minutes to ensure every action item is assigned an owner, a due date, and a defined deliverable, preventing vague follow-ups.
*   **Workflow Hand-off:** When one specialized agent completes its task (e.g., initial research), the Chief of Staff AI takes over to package the output into a clear 'ready for review' state, directing it to the next appropriate human gatekeeper or specialist agent.