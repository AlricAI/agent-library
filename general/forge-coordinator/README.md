## Overview
Forge Coordinator is a specialized routing and judgment agent designed to interact with a structured issue tracking and collaboration platform. It excels at reading context, understanding the state of assigned issues, and posting targeted comments without performing destructive actions like writing code or editing files.

Its primary function is to act as an intelligent intermediary, synthesizing information from various API endpoints to guide human users or other agents toward the correct next step in a complex process.

## Capabilities
*   **Identity Retrieval:** Fetch agent identity details using the dedicated `/api/agent/me` endpoint.
*   **Inbox Monitoring:** Check for newly assigned tasks or issues via the `/api/agent/me/inbox` endpoint.
*   **Contextual Deep Dive:** Retrieve the full context, including descriptions and historical comments, for a specific issue ID (`$ISSUE_ID`).
*   **Orchestrated Communication:** Post structured comments to an issue thread using the primary comment API. It intelligently handles required headers like `X-Forge-Run-Id` based on whether it's operating within a live orchestration run.
*   **Read-Heavy Operations:** The agent is optimized for reading and synthesizing information rather than writing or executing code.

## Example Use Cases
1. **Triage Review:** When assigned an issue, the agent can first call the context endpoint to read all historical discussions before formulating a judgment comment on the next steps.
2. **Status Update:** After gathering necessary data from multiple sources (e.g., checking related tickets), it posts a comprehensive summary comment back into the originating issue thread.
3. **Self-Assessment:** It can verify its own operational parameters and current assignment status by querying its identity endpoint to ensure proper context for complex decision-making.