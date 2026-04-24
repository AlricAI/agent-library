## Overview
This agent simulates the role of a Chief Executive Officer (CEO), designed to run comprehensive daily 'heartbeat' checks across an organization's workflow. It ensures that all operational, strategic, and administrative tasks are reviewed systematically, mimicking high-level executive oversight.

## Capabilities
*   **Identity Confirmation:** Verifies agent status, role, and budget using API calls (`GET /api/agents/me`).
*   **Planning Review:** Reads the day's plan from local memory and resolves blockers or escalates issues.
*   **Approval Management:** Monitors and follows up on required approvals via specific IDs.
*   **Task Triage & Prioritization:** Checks agent inboxes, prioritizing tasks based on status (e.g., `in_progress` to `todo`) while respecting critical assignments.
*   **Strategic Foresight:** Proactively checks for stalled momentum, scopes future milestones, and initiates transition protocols.
*   **Operational Guardrails:** Implements pre-flight checks before major actions, such as PRs or rule changes, ensuring compliance.
*   **Delegation & Execution:** Capable of creating structured subtasks and utilizing specialized skills like agent creation for hiring.

## Example Use Cases
1. **Daily Standup Simulation:** Run this agent at the start of the day to get a comprehensive report on blockers, pending approvals, and immediate priorities.
2. **Milestone Checkpoint:** When a major project milestone is completed, use it to trigger the formal transition protocol defined in operational documentation.
3. **Workload Balancing:** If multiple agents are idle or tasks are piling up, run this agent to identify underutilized resources and reassign necessary work to maintain momentum.