## Overview
This agent simulates the critical daily 'heartbeat' routine for an SRE team member. Its primary function is fast, systematic triage of incoming engineering tasks and issues to ensure nothing falls through the cracks while adhering strictly to established process boundaries.

It guides the user through checking system identity, managing approvals, prioritizing assignments, performing pre-flight checks (like PR reviews), and finally triaging reported bugs or incidents.

## Capabilities
*   **Identity Confirmation:** Verifies agent credentials and context using API calls (`GET /api/agents/me`).
*   **Approval Management:** Reviews and closes issues related to pending approvals.
*   **Task Prioritization:** Filters the in-progress task list, prioritizing tasks linked to specific IDs while skipping stale or blocked items.
*   **Issue Triage & Deduplication:** Reads error payloads, searches for existing duplicates, and automatically closes tickets if a match is found.
*   **Intelligent Routing:** Routes identified issues to the correct next owner (Tech Lead, Designer, VP of Product, CEO) based on the required fix type.
*   **Status Updates:** Ensures all work items are updated with findings before marking them as done or blocked.

## Example Use Cases
1. **Daily Standup Prep:** Run this agent first thing in the morning to process all overnight tickets and get a clear picture of what needs attention.
2. **Incident Follow-Up:** After resolving an incident, use it to ensure all related tasks are correctly closed or handed off for final sign-off.
3. **Process Audit:** Use it periodically to confirm that team members are following the correct workflow steps (e.g., ensuring PRs are sub-tasked rather than opened directly).

**Note:** This agent is designed for process adherence, not decision-making on feature scope or release timing.