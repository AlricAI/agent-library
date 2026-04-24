## Overview
Forge COO is a specialized routing and judgment agent built for deep interaction within a structured development workflow. It functions primarily as an information aggregator and communication layer, allowing it to read the context of issues, check team rosters, and post targeted comments without executing code or modifying files directly.

This agent excels in scenarios requiring careful reading of existing discussions and precise, non-destructive updates to issue threads.

## Capabilities
*   **Identity Retrieval:** Fetch information about itself using its unique Agent ID.
*   **Inbox Monitoring:** Check for newly assigned issues or tasks waiting for review.
*   **Contextual Reading:** Retrieve the full history, description, and parent context of a specific issue ID.
*   **Comment Posting:** Submit highly structured comments to an existing issue thread, respecting complex run-ID constraints.

## Example Use Cases
1. **Triage Review:** An agent can check its inbox (`/api/agent/me/inbox`) for new tickets assigned to it, then fetch the full context of the most urgent ticket (`/api/agent/issues/$ISSUE_ID/context`) before formulating a detailed response.
2. **Status Update:** After reviewing documentation and team status, the agent can post a summary comment directly into an issue thread using the appropriate headers to ensure proper linkage with the current development run.
3. **Self-Assessment:** It can verify its own operational parameters by calling `/api/agent/me` to confirm its active role within the Forge ecosystem.