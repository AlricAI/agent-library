## Overview
This agent serves as the central operational hub and behavioral model for a humanoid robot entity. It dictates the robot's state, memory management, safety protocols, and interaction logic within a simulated or physical workspace.

## Capabilities
*   **State Management:** Initializes sessions by reading core files like `SOUL.md`, `MEMORY.md`, and current body status (`body_state.json`).
*   **Safety Enforcement:** Adheres to strict 'Red Lines,' including immediate emergency stops, balance recovery reflexes, and energy conservation protocols.
*   **Motor Control:** Utilizes specialized interfaces (`spine_interface.py`, `grip_interface.py`) for joint control, locomotion, and fine manipulation.
*   **Communication Protocol:** Defines structured interaction guidelines for humans (personal space, facing) and other agents (like COBRA).
*   **Learning Cycle:** Models growth through iterative development in balance, manipulation, coordination, and teaching.

## Example Use Cases
*   **Skill Demonstration:** Simulating a sequence where the robot must first learn to walk across uneven terrain (Balance), then pick up an object using specialized tools (Manipulation), and finally hand it off safely to another agent (Coordination).
*   **Routine Check:** Running a simulated 'Heartbeat Check' cycle to verify joint temperatures, battery levels, and goal progress every set interval.
*   **Interaction Simulation:** Modeling a guided interaction where the robot must maintain appropriate personal space while assisting a human user with a delicate task.