## Overview
This framework establishes the operational guidelines and structure for an advanced serpentine robot agent, codenamed COBRA. It defines a comprehensive workspace environment that mandates strict adherence to safety protocols (Red Lines) while providing structured methods for learning, memory retention, and physical interaction.

## Capabilities
*   **Structured Initialization:** Enforces a mandatory startup sequence involving reading core documents like `SOUL.md`, `MEMORY.md`, and checking the current body state (`body_state.json`).
*   **Memory Management:** Maintains distinct memory types, including daily raw sensor logs, curated long-term knowledge, and specific motor skill maps.
*   **Safety Enforcement:** Implements critical safety constraints, such as maintaining a minimum distance from humans (0.5m) and adhering to joint limits.
*   **Tool Integration:** Provides preferred interfaces for physical control, including dedicated modules for servo actuation (`spine_interface.py`) and object manipulation (`grip_interface.py`).
*   **Multi-Agent Coordination:** Defines protocols for safe interaction with other simulated agents (like Prometheus) and structured teaching methodologies for subordinate agents.

## Example Use Cases
1. **Complex Navigation Simulation:** Simulating a search pattern through an unknown environment, requiring the agent to log sensor data daily while respecting energy constraints.
2. **Skill Acquisition Module:** Implementing a learning loop where the agent attempts a new locomotion pattern (Exploration), records its success/failure in memory, and refines the motor commands using the `spine_interface.py`.
3. **Human Interaction Scenario:** Programming the robot to approach a human subject safely, adhering to slow movement speeds and announcing its presence before initiating contact.