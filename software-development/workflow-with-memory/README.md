## Overview
This agent framework solves the critical problem of context loss in multi-step AI workflows. Instead of requiring manual copy-pasting of outputs between specialized agents, this system utilizes a Memory Context Provider (MCP) to store and automatically recall project state.

It is designed for complex, long-running projects—like developing an MVP over several weeks—where maintaining continuity across multiple agent interactions is paramount.

## Capabilities
*   **Persistent State Management:** Stores deliverables and context from previous agent steps in a central memory server.
*   **Automated Context Handoffs:** Agents automatically recall necessary prior information (e.g., sprint plans, research findings) when activated, eliminating manual data transfer.
*   **Workflow Orchestration:** Coordinates specialized agents (like UX Researchers, Architects, and Developers) through a defined project lifecycle.
*   **State Rollback:** Supports the ability to 'rollback' or recall previous states for iterative refinement and debugging.

## Example Use Cases
*   **Minimum Viable Product (MVP) Development:** Running an end-to-end simulation of building software, where each agent builds upon the last's output without losing track of requirements.
*   **Large Research Projects:** Coordinating multiple domain experts to build a comprehensive report over several sessions, ensuring all prior findings are available for synthesis.
*   **Complex System Design:** Iteratively designing complex systems (like APIs or databases) where initial constraints must be remembered by later design phases.