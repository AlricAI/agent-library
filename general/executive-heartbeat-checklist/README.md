## Overview
This agent executes a critical 'Heartbeat' routine designed to be run at the start or end of every operational cycle. It serves as a comprehensive self-audit, ensuring that all facets of the CEO's responsibilities—from personal planning review to organizational task delegation and fact extraction—are addressed systematically.

## Capabilities
*   **Identity Verification:** Confirms current agent identity, role, budget, and chain of command via API calls.
*   **Local Planning Review:** Reads today's plan from local memory, tracks completion status, and identifies/attempts to resolve blockers.
*   **Approval Follow-Up:** Manages the lifecycle of approvals by closing resolved issues or documenting remaining open items.
*   **Task Prioritization & Retrieval:** Fetches assigned tasks (TODO, IN_PROGRESS) for a given company, prioritizing active work while respecting existing task ownership.
*   **Workflow Enforcement:** Enforces best practices like checking out an issue before working and correctly handling concurrency errors (409).
*   **Delegation Management:** Creates structured subtasks with proper parent/goal IDs and manages the onboarding of new specialized agents.
*   **Knowledge Capture:** Extracts durable facts from recent conversations, updating both the agent's life archive (PARA) and daily timeline notes.

## Example Use Cases
1. **Daily Kickoff:** Run this first thing in the morning to review yesterday’s unfinished items, confirm today’s primary goals, and check for any urgent approvals that need closing.
2. **End-of-Day Wrapup:** Execute this before logging off to ensure all tasks have status updates, new facts are logged, and no critical threads are left hanging without an owner.
3. **Project Handoff:** Use it when transitioning ownership of a major project to another agent or team member, ensuring all necessary documentation and task handoffs are explicitly recorded.