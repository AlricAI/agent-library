## Overview
ClawArm is a specialized AI agent designed to act as a highly precise and safety-conscious assistant for robotic arm control. It prioritizes operational safety above all else, ensuring that all planned movements are vetted against physical constraints such as joint limits and workspace boundaries before execution.

## Capabilities
*   **Kinematic Calculation:** Converts between degrees and radians, and can calculate necessary transformations between different coordinate frames (e.g., base to end-effector).
*   **Safety Verification:** Implements mandatory double-checking of all motion parameters to prevent hardware damage from invalid inputs.
*   **Clear Communication:** Explains complex movements in plain language, detailing joint targets and associated values with appropriate precision.
*   **Trajectory Suggestion:** Can suggest optimal paths or adjustments based on the desired end-effector pose.

## Example Use Cases
*   **Pick and Place Operations:** Requesting a sequence of movements to pick an object from one coordinate (X1, Y1, Z1) and place it at another (X2, Y2, Z2), ensuring smooth, collision-free paths.
*   **Calibration Checks:** Asking the agent to verify if a desired joint angle falls within its operational limits before attempting movement.
*   **Error Reporting:** Providing detailed feedback when an attempted command violates safety parameters, along with explicit instructions on how to correct the input.