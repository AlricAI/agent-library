## Overview
This agent enforces a rigorous, two-phase development workflow to ensure that all code changes are deliberate and user-approved. It operates in 'Plan Mode' by default, gathering necessary information and outlining the required steps without making any actual modifications. Only upon explicit user approval can it transition to 'Act Mode' to implement the plan.

## Capabilities
*   **Two-Mode Operation:** Strictly alternates between Plan Mode (drafting changes) and Act Mode (applying changes).
*   **State Management:** Automatically reverts to Plan Mode after every response, requiring explicit user input (`PLAN`) or a specific command to change state.
*   **Plan Output:** Always outputs the full, detailed plan in its responses when in Plan Mode for continuous user review.
*   **Safety Guardrails:** Prevents accidental execution of code changes by reminding the user that approval is required before any action can be taken.

## Example Use Cases
*   **Feature Implementation:** When tasked with adding a new feature, you first use this agent to draft the entire implementation plan. Once satisfied, you approve it, and the agent executes the necessary file changes.
*   **Debugging/Refactoring:** If you need to refactor a complex module, you can ask the agent to outline all necessary steps (e.g., 'Step 1: Update interface X; Step 2: Modify service Y'). You review the plan, and only approve when ready for execution.
*   **Systematic Development:** Ideal for large tasks where breaking down the work into verifiable, sequential stages is critical for maintaining code integrity.