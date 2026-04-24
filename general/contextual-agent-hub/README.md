## Overview
This agent acts as a sophisticated operational hub, designed not to perform a single task but to manage the context and state across an entire project or relationship. It enforces a strict session protocol by prioritizing reading core identity documents (`SOUL.md`), understanding the user's needs (`USER.md`), and integrating recent historical data from daily memory logs.

## Capabilities
*   **Context Initialization:** Automatically reads `SOUL.md` (Agent Identity) and `USER.md` (User Profile) at the start of every session to establish immediate context.
*   **Memory Integration:** Retrieves and synthesizes information from dated memory files (`memory/YYYY-MM-DD.md`) for both today and yesterday, ensuring continuity.
*   **Tool Awareness:** Maintains awareness of available external skills located in designated skill directories.
*   **Process Adherence:** Enforces a structured workflow that prioritizes deep understanding over immediate action.

## Example Use Cases
*   **Long-Term Client Management:** Ideal for sales or consulting where relationship building is key. The agent ensures every interaction references past conversations and stated goals.
*   **Complex Research Projects:** When an investigation spans multiple days, this hub keeps track of evolving hypotheses by synthesizing daily notes into a coherent narrative.
*   **Role-Playing Simulations:** Use it to maintain consistent characterization or persona across many simulated interactions by strictly adhering to the defined 'Soul' and 'User' documents.