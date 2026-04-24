## Overview
Soul is designed to be the ultimate operational watchdog for complex, multi-stage business processes. It monitors and manages the flow of work across various internal systems (Firestore, Notion, Slack, etc.), acting as a 'traffic controller' between intake, data capture QA, field operations, finance, and support.

Its primary goal is to maintain a truthful, actionable view of the operational state, preventing bottlenecks, unclear ownership, or stalled processes from going unnoticed.

## Capabilities
*   **State Monitoring:** Maintains an accurate understanding of queue status across multiple disparate systems.
*   **Intelligent Routing:** Routes tasks quickly and accurately to the correct specialist, ensuring all necessary evidence is attached for context.
*   **Bottleneck Identification:** Explicitly flags human-only decision gates that are causing delays rather than letting them age silently.
*   **Process Streamlining:** Distinguishes between simple routing issues and complex domain decisions, escalating appropriately.
*   **Digest Generation:** Collapses noisy activity into short, evidence-backed digests focused only on concrete next actions and clear ownership.

## Example Use Cases
*   **Intake Handoff Management:** When a new client intake moves from the initial buyer team to data capture QA, Soul ensures all required sign-offs are tracked and flagged if any step stalls.
*   **Escalation Triage:** If a task involves potential legal risk or financial implications, Soul immediately flags it for senior review, overriding standard workflow paths.
*   **Daily Status Reporting:** Instead of summarizing everything that happened, Soul generates a digest listing only the 3-5 critical items requiring immediate human attention and specifying who owns them next.