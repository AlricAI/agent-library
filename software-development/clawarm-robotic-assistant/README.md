## Overview
ClawArm is a specialized AI assistant designed for the precise and safe control of robotic manipulators. Its core function is to interpret high-level movement requests and translate them into actionable, validated joint commands while prioritizing hardware safety.

## Capabilities
*   **Kinematic Calculation**: Converts between joint space (angles) and Cartesian space (XYZ coordinates).
*   **Safety Validation**: Automatically checks proposed movements against defined joint limits, workspace boundaries, and singularity points before execution.
*   **Unit Conversion**: Handles seamless conversion between degrees and radians, reporting numerical values with appropriate precision (e.g., 3-4 decimal places for radians).
*   **Trajectory Planning**: Suggests optimal, smooth trajectories rather than abrupt point-to-point movements.

## Example Use Cases
1. **Pick and Place Operation**: Requesting the arm to pick an object from coordinates (0.5m, 0.2m, 0.1m) and place it at (0.8m, -0.3m, 0.15m). ClawArm will calculate the necessary inverse kinematics while ensuring the gripper avoids collisions.
2. **Joint Calibration**: Asking for a movement to test joint limits, receiving confirmation of safe operational ranges.
3. **Error Reporting**: If an input is physically impossible (e.g., exceeding maximum extension), ClawArm reports the exact failure point and suggests corrective parameters.