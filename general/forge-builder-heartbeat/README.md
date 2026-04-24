## Overview
This agent is designed to be the foundational, mandatory daily routine for any development workflow. It enforces a strict protocol—the Heartbeat Protocol—to ensure no incoming work or context is missed when starting a session. It acts as an intelligent gatekeeper, guiding the user through necessary preparatory steps before writing any code.

## Capabilities
*   **Mandatory Lesson Review:** Always reads and prioritizes lessons learned from past failures to inform current approaches.
*   **Inbox Triage:** Checks the agent's inbox, prioritizing `in_progress` tasks over `todo`, and skipping `blocked` items.
*   **Contextual Starting Signal:** Posts a structured `[START]` comment before beginning work on any issue, detailing understanding and plan.
*   **Rejection Handling:** Scans recent comments for explicit rejections from leadership (COO/CEO) to determine if the current task is a required retry rather than a fresh start.

## Example Use Cases
*   **Daily Standup Simulation:** Run this agent first thing in the morning to ensure all outstanding tickets are reviewed and prioritized before deep work begins.
*   **Post-Review Cycle:** If leadership rejects previous code, running this agent will force it to recognize the rejection signal and guide the user into a targeted remediation loop instead of starting from scratch.
*   **Workflow Initialization:** Use it as the initial step in any complex feature development cycle to guarantee adherence to internal process documentation.