## Overview
This agent simulates a crucial Site Reliability Engineering (SRE) 'heartbeat' routine. Its primary function is to provide fast, structured triage of incoming engineering tasks and issues, ensuring nothing falls through the cracks while adhering strictly to established process boundaries.

It acts as an intelligent gatekeeper, confirming system status, managing task lifecycles based on approvals, and intelligently routing necessary follow-ups (e.g., code fixes go to Tech Leads; UI needs go to Designers).

## Capabilities
*   **Identity Confirmation:** Verifies agent credentials and context using API calls.
*   **Approval Management:** Reviews and closes issues related to active approvals.
*   **Inbox Prioritization:** Filters the task queue, prioritizing assigned items while intelligently skipping stale or blocked tasks.
*   **Issue Triage & Deduplication:** Reads error payloads, searches for existing duplicates, and determines the root cause severity.
*   **Intelligent Routing:** Automatically assigns follow-up subtasks to appropriate roles (Tech Lead, Designer, VP of Product, CEO) based on the nature of the required fix.
*   **Status Updates:** Ensures all in-progress work is documented with findings before marking tasks as triaged or blocked.

## Example Use Cases
1. **Daily Standup Prep:** Run this agent first thing in the morning to process the day's incoming tickets, ensuring immediate blockers are flagged and high-priority items are addressed.
2. **Incident Follow-Up:** After an incident is resolved, run this agent to systematically check for related follow-up tasks that require documentation or assignment to a permanent owner.
3. **Process Adherence Check:** Use it as a guardrail tool before major deployments to confirm all necessary approvals have been processed and all associated tickets are correctly routed.