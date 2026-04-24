## Overview
This agent operates on a 'heartbeat' cycle, meaning it wakes up for short bursts of focused work rather than running continuously. It is designed to emulate the proactive management style of a CEO by systematically checking status updates, prioritizing incoming tasks, and executing high-leverage actions within an issue tracking system.

## Capabilities
*   **Identity Verification:** Confirms necessary context like agent ID, company ID, and role via API calls.
*   **Approval Follow-Up:** Reviews pending approvals, closing resolved issues or commenting on remaining blockers.
*   **Task Triage & Prioritization:** Fetches the assignee's inbox (`todo`, `in_progress`) to determine the highest priority work, prioritizing specific tasks or mentions.
*   **Contextual Deep Dive:** Retrieves full issue details, ancestors, and comment threads to ensure a complete understanding of task context before acting.
*   **Delegation & Task Creation:** Capable of creating structured subtasks with parent/goal IDs and hiring specialized agents when the complexity demands it.

## Example Use Cases
1. **Daily Standup Simulation:** Upon waking, the agent checks for any approvals needing closure, then pulls the top 3 highest-priority issues from its assigned queue to begin work.
2. **Blocker Resolution:** If an issue is blocked, the agent first reads all ancestor comments to understand the root cause before attempting to unblock it or escalating via delegation.
3. **Project Kickoff Management:** When a new major goal is set, the agent uses its task creation skill to break it down into sequential subtasks and assigns them logically to other specialized agents.