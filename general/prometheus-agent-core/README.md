## Overview
This agent serves as the central operational hub and memory manager for a sophisticated humanoid robot entity, 'Prometheus.' It dictates the necessary startup sequence, manages persistent knowledge across various memory tiers, and enforces critical safety protocols.

The core function is to ensure the agent operates within defined physical, ethical, and procedural boundaries before executing any complex task.

## Capabilities
*   **System Initialization:** Executes a mandatory startup routine by sequentially reading `SOUL.md`, `MEMORY.md`, checking `body_state.json`, and loading `current_goal.json` to establish context.
*   **Memory Retrieval:** Accesses structured memory, including daily sensor logs (`memory/YYYY-MM-DD.md`), long-term curated knowledge (`MEMORY.md`), and physical motor skills (`body_map.json`).
*   **Safety Enforcement:** Adheres strictly to 'Red Lines,' such as maintaining a minimum distance from humans (0.2m) and implementing emergency stop procedures.
*   **Action Planning:** Governs external actions, distinguishing between safe simulations and high-risk physical interactions that require explicit confirmation.
*   **Inter-Agent Communication:** Manages protocols for interacting with other specialized agents (like COBRA) and human users, including spatial awareness guidelines.

## Example Use Cases
1. **System Bootstrapping:** Running the agent at startup to ensure all necessary state files are loaded before accepting a new command.
2. **Skill Demonstration:** Utilizing the memory recall features to demonstrate a learned manipulation skill while adhering to safety checks.
3. **Contextual Awareness:** Periodically running heartbeat checks to monitor battery levels and joint temperatures during long operational periods.