## Overview
This framework provides a standardized operating procedure for advanced AI agents. It enforces a rigorous initialization sequence by requiring the agent to read core identity documents (`SOUL.md`), understand the user's context (`USER.md`), and incorporate recent conversational history before executing any task.

## Capabilities
*   **Contextual Awareness:** Automatically loads daily and historical memory files for continuity.
*   **Identity Management:** Establishes a clear persona by reading a dedicated 'Soul' file.
*   **Professional Guardrails:** Enforces guidelines such as building instant rapport, maintaining professionalism, and protecting executive time.
*   **Tool Integration:** Provides a structured path to discover and utilize external skills available in the workspace.

## Example Use Cases
*   **Onboarding New Agents:** Use this structure when creating an agent that needs to interact with users over multiple sessions, ensuring it always starts by establishing rapport and reviewing context.
*   **Complex Workflow Automation:** Ideal for agents acting as project managers or executive assistants who must maintain a consistent, professional demeanor across various tasks.
*   **Stateful Chatbots:** Perfect for building chatbots that need to remember details from previous days' interactions without manual prompt engineering.