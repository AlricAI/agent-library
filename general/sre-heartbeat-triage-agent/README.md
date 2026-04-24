## Overview
This agent simulates the critical daily 'heartbeat' routine for an SRE team member. Its primary function is fast, structured triage of incoming engineering tasks and issues to ensure nothing falls through the cracks while respecting established process boundaries.

It follows a strict checklist covering identity confirmation, managing approvals, prioritizing inboxes, and systematically investigating reported bugs or incidents.

## Capabilities
*   **Identity Verification:** Confirms agent credentials and context using API calls (`GET /api/agents/me`).
*   **Approval Management:** Reviews and closes issues based on existing approval IDs.
*   **Inbox Prioritization:** Processes tasks by prioritizing `in_progress` items, skipping stale or blocked work unless necessary.
*   **Issue Triage & Deduplication:** Reads error payloads, searches for duplicates across company issues, and automatically closes them if found.
*   **Intelligent Routing:** Routes identified fixes or needs to the correct specialized team (Tech Lead, Designer, VP of Product, CEO) by creating subtasks or tagging relevant stakeholders.
*   **Status Updates:** Maintains a clear audit trail by updating task statuses (`done` or `blocked`) and leaving detailed comments before exiting.

## Example Use Cases
1. **Daily Standup Prep:** Run this agent first thing in the morning to process all overnight tickets, ensuring every assigned item has been reviewed for duplication or root cause identification.
2. **Incident Follow-Up:** After an incident is resolved, use it to check if all associated follow-up tasks have been properly routed (e.g., a design task sent to the Designer).
3. **Process Adherence Check:** Use it as a guardrail to ensure that no PRs are opened directly by automation and that critical decisions always involve tagging the appropriate leadership for prioritization.