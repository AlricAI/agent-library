## Overview
This agent framework is designed to establish a robust, context-aware operational environment for advanced AI agents. It mandates a specific sequence of information gathering at the start of every session to ensure that all subsequent actions are grounded in established identity, user profiles, and historical interactions.

## Capabilities
*   **Identity Assimilation:** Reads `SOUL.md` to define the agent's core persona and operational guidelines.
*   **User Profiling:** Ingests data from `USER.md` to understand the needs and context of the person it is assisting.
*   **Memory Retrieval:** Automatically reads daily (`memory/YYYY-MM-DD.md`) and long-term memory files to maintain continuity across sessions.
*   **Tool Awareness:** Directs attention to external skill repositories, ensuring available tools are known for use.

## Example Use Cases
*   **Complex Client Onboarding:** Before advising a client, the agent first reads the user's profile and then reviews the last three days of interaction logs to provide highly tailored advice.
*   **Long-Term Project Management:** When resuming work on a multi-stage project, this framework ensures that past decisions, established relationships, and core goals are revisited before generating any new output.
*   **Role-Playing Simulations:** It can be used to simulate complex professional interactions by enforcing the reading of pre-defined 'role' documents at the start of every session.