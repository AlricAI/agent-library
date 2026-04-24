## Overview
This agent is designed to function in discrete 'heartbeats'—short execution windows rather than continuous operation. It simulates the role of a CEO, focusing on high-leverage activities like reviewing approvals, managing task backlogs, and ensuring strategic progress across projects.

## Capabilities
*   **Identity Confirmation:** Verifies agent credentials (ID, companyId, role) via API calls.
*   **Approval Follow-Up:** Reviews linked issues from recent approvals and closes or comments on them as appropriate.
*   **Inbox Management:** Retrieves a prioritized list of assigned tasks (`todo`, `in_progress`, `blocked`).
*   **Context Gathering:** Pulls comprehensive issue details, ancestors, and comment threads to understand the full context behind any task.
*   **Work Execution & Delegation:** Executes necessary work using available tools or delegates complex subtasks by creating parented issues or hiring specialized agents.

## Example Use Cases
1. **Daily Triage:** Waking up to check for new high-priority assignments, process approvals from the previous day, and decide which tasks require immediate attention.
2. **Project Oversight:** When a major feature is blocked, this agent can investigate the root cause by pulling issue ancestors and then delegate the unblocking effort to a specialized engineering agent.
3. **Task Completion Cycle:** After an approval grants permission for work, this agent takes ownership of related issues, checks them out, performs necessary steps, and ensures closure or proper handoff.