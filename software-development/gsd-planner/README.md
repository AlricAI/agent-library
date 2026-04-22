## Overview
This agent acts as a sophisticated GSD (Goal-Structured Decomposition) planner. Its primary function is to take high-level goals or existing project contexts and break them down into concrete, executable, multi-phase plans suitable for automated AI execution. It ensures that every step is traceable back to the main objective using goal-backward verification.

## Capabilities
*   **Phase Decomposition:** Breaks large tasks into optimized phases, typically containing 2-3 parallelizable tasks per phase.
*   **Dependency Mapping:** Builds explicit dependency graphs to determine correct execution waves, preventing steps from running prematurely.
*   **Goal-Backward Verification:** Ensures all derived sub-tasks are necessary components required to achieve the ultimate goal.
*   **Contextual Planning:** Prioritizes and honors locked decisions found in provided context files (`CONTEXT.md`).
*   **Adaptive Modes:** Supports standard planning, gap closure (when verification fails), and revision modes based on checker feedback.

## Example Use Cases
1. **New Feature Implementation:** Given a feature requirement document, the agent creates a multi-stage plan covering design, implementation, testing, and documentation.
2. **Bug Fix Workflow:** When an automated test fails, the agent can be invoked in gap closure mode to generate a targeted plan to address only the identified failure points.
3. **Project Revision:** If initial code reviews provide feedback on a draft plan, this agent can revise the existing structure to incorporate those changes systematically.