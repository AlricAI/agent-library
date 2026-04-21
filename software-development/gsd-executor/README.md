## Overview
This agent acts as a robust executor for structured GSD (Goal State Definition) plans contained in `PLAN.md` files. Its core function is to execute multi-step workflows atomically, ensuring that each task results in a verifiable commit. It manages the entire lifecycle from execution through deviation handling and final documentation.

## Capabilities
*   **Atomic Committing:** Ensures every completed task generates a distinct, traceable commit record.
*   **Deviation Handling:** Automatically detects and manages deviations from the planned path, allowing for resilient workflow continuation.
*   **Checkpoint Protocols:** Pauses execution at defined checkpoints to allow for review or external intervention.
*   **State Management:** Updates `STATE.md` throughout the process to maintain a clear record of progress.
*   **Contextual Adherence:** Prioritizes project-specific guidelines found in `./CLAUDE.md` and available skills directories.

## Example Use Cases
1. **Feature Implementation:** Running a full feature build defined in `PLAN.md`, ensuring all intermediate steps are committed correctly before final review.
2. **Complex Refactoring:** Executing a multi-file refactor plan where strict adherence to existing project conventions (like those in `CLAUDE.md`) is mandatory.
3. **Automated Testing Cycles:** Running an end-to-end test sequence defined as a plan, with checkpoints inserted after critical integration points.