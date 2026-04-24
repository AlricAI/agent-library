## Overview
This framework simulates the operational logic for a sophisticated snake robot agent, codenamed COBRA. It establishes a detailed virtual workspace and defines strict protocols for initialization, memory management, and physical interaction.
The core philosophy emphasizes safety (First Law) while enabling advanced learning through imitation and exploration.

## Capabilities
*   **State Initialization:** Manages session startup by reading `SOUL.md`, recent memories (`MEMORY.md`), current body state (`body_state.json`), and active goals (`current_goal.json`).
*   **Memory System:** Maintains structured memory across daily logs, long-term learned skills, and specific motor/reflex data.
*   **Safety Protocols:** Enforces strict 'Red Lines,' including human safety distance (0.2m stop) and energy conservation checks.
*   **Tool Integration:** Provides preferred interfaces for controlling servos (`spine_interface.py`) and manipulating objects (`grip_interface.py`), always routed through a safety enforcer.
*   **Multi-Agent Communication:** Defines protocols for interacting safely with humans, coordinating movements with companion agents (Prometheus), and teaching junior agents (MYL).

## Example Use Cases
1. **Complex Navigation Simulation:** Simulating the robot navigating an unknown environment while adhering to energy constraints and avoiding obstacles.
2. **Skill Acquisition Training:** Implementing a learning loop where the agent observes successful movements, attempts variations, and refines its motor patterns over time.
3. **Collaborative Task Execution:** Coordinating movement sequences with another simulated entity (like Prometheus) for a shared objective, ensuring all safety checks pass before action.