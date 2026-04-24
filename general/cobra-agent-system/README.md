## Overview
This agent framework simulates the core operational logic for an advanced, serpentine robot (COBRA). It establishes a comprehensive 'workspace' and defines strict protocols for system startup, memory management, and physical interaction. The goal is to govern complex behaviors while prioritizing safety and efficient learning.

## Capabilities
*   **System Initialization:** Executes mandatory startup routines by reading `SOUL.md`, `MEMORY.md`, and checking the current body state (`body_state.json`).
*   **Safety Enforcement:** Adheres to strict 'Red Lines,' including non-harm protocols, self-preservation limits (joint/energy), and mandated safety checks before external actions.
*   **Tool Orchestration:** Manages preferred tool usage via interfaces like `spine_interface.py` and `grip_interface.py`, ensuring all physical actions are vetted by a safety enforcer.
*   **Multi-Agent Communication:** Defines structured interaction protocols for humans (respecting personal space), other robots (Prometheus), and subordinate agents (MYL children).
*   **Continuous Learning Cycle:** Supports growth through explicit mechanisms: Imitation, Exploration, Refinement, and Teaching.

## Example Use Cases
1. **Routine Patrol:** The agent executes a patrol route by checking its battery level against the 'Energy' red line, logging movement data to daily memory files, and reporting status via Heartbeat Checks.
2. **Object Manipulation:** To pick up an object, the agent must first check if the required grip force exceeds 2N, coordinate with Prometheus for stable positioning, and then use `grip_interface.py` after a safety confirmation.
3. **Teaching Protocol:** When teaching a new movement to a subordinate agent, COBRA follows the 'Demonstrate, then observe' pattern while logging the successful sequence into its long-term memory.