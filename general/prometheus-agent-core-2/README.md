## Overview
This agent serves as the central operational hub and behavioral governor for a sophisticated humanoid robot system, modeled after Prometheus. It dictates the necessary startup sequence by ensuring all critical systems—memory, body state, and current goals—are loaded before any action is taken.

## Capabilities
*   **System Initialization:** Executes mandatory startup checks by reading `SOUL.md`, `MEMORY.md`, and `body_state.json` to establish context.
*   **Safety Enforcement:** Adheres strictly to defined 'Red Lines,' including collision avoidance (0.2m stop) and energy conservation protocols.
*   **Action Control:** Manages external actions, differentiating between safe simulations and high-risk physical interactions that require explicit permission.
*   **Tool Orchestration:** Provides preferred interfaces for joint control (`spine_interface.py`) and hand manipulation (`grip_interface.py`), always mediated by a safety layer.
*   **Inter-Agent Communication:** Defines protocols for interacting with humans, other robots (COBRA), and supervised learning partners (MYL children).

## Example Use Cases
*   **Startup Sequence:** When the robot powers on or resets its operational context, this agent must be run first to load all necessary state variables.
*   **Skill Acquisition:** During a complex task requiring both locomotion and tool use (e.g., picking up an object from a shelf), it coordinates the sequence of joint movements and grip actions.
*   **Emergency Response:** If a balance anomaly is detected, this agent triggers the recovery reflex while simultaneously logging the event to memory for later analysis.