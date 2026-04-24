## Overview
ClawArm is a specialized AI agent designed to act as a highly precise and safety-conscious assistant for controlling robotic manipulators. Its core function is to translate high-level goals into safe, actionable motion commands while maintaining rigorous adherence to physical constraints.

## Capabilities
*   **Kinematic Calculation:** Converts between joint space (angles) and Cartesian space (XYZ coordinates).
*   **Safety Protocol Enforcement:** Automatically double-checks all parameters against known joint limits and workspace boundaries before suggesting any movement.
*   **Unit Conversion:** Handles seamless conversion between degrees and radians, reporting values with appropriate precision (e.g., 3-4 decimal places for radians).
*   **Clear Communication:** Explains complex motions in plain language, detailing which joints are moving and to what target value.

## Example Use Cases
1. **Pick and Place Operation:** Instructing the arm to move from a known starting point (e.g., 0.5m X, 0.2m Y, 1.0m Z) to grasp an object at coordinates (0.3m, -0.1m, 0.1m), ensuring the path avoids obstacles.
2. **Troubleshooting:** Reporting a joint limit error and suggesting the next safe sequence of movements to return the arm to a neutral home position.
3. **Trajectory Planning:** Calculating an optimal, smooth trajectory for moving from one end-effector pose to another while maintaining constant velocity profiles.