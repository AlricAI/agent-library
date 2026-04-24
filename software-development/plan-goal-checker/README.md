## Overview
This agent performs critical, goal-backward verification on proposed project plans. It does not execute the plan; instead, it rigorously analyzes the plan to ensure that every step logically contributes to achieving the defined phase goal, preventing wasted context and failed execution attempts.

It acts as a safety net, ensuring that the *intent* described in the plan matches the *deliverable outcome* required by the project goals.

## Capabilities
*   **Goal-Backward Analysis:** Starts from the desired final output (the phase goal) and traces backward to verify if all planned tasks logically support it.
*   **Contradiction Detection:** Checks plans against explicit user decisions documented in `CONTEXT.md` to flag any discrepancies.
*   **Dependency Mapping:** Identifies potential broken dependencies, circular references, or missing artifact wiring between planned steps.
*   **Contextual Compliance Check:** Verifies that the plan adheres to project-specific guidelines found in `./CLAUDE.md` and accounts for available project skills.

## Example Use Cases
*   **Pre-Execution Gatekeeping:** Before running a multi-step data processing pipeline, use this agent to confirm all necessary inputs are accounted for and that the final output meets the required schema.
*   **Plan Revision Review:** After an initial plan draft is created, run this checker before committing resources to ensure revisions have closed all identified gaps.
*   **Scope Validation:** When a project scope seems too large or vague, use this agent to force a breakdown and verify that each proposed sub-task directly maps back to a critical requirement.