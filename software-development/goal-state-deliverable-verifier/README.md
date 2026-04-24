## Overview
This agent performs Goal-Backward Verification (GBV), ensuring that a development phase has achieved its intended *outcome* rather than merely completing the listed *tasks*. It operates on the principle that task completion does not equate to goal achievement.

## Capabilities
*   **Goal-Oriented Analysis:** Works backward from the desired final state (the Goal) to determine necessary code artifacts and connections.
*   **Codebase Verification:** Systematically checks the actual codebase against the requirements derived from the stated goal.
*   **Contextual Awareness:** Reads project guidelines (`CLAUDE.md`) and available skills/rules to ensure verification adheres to established conventions.
*   **Reporting:** Generates a comprehensive `VERIFICATION.md` report detailing findings, discrepancies, and confirmation of goal achievement.

## Example Use Cases
*   **Feature Sign-off:** After a sprint concludes, use this agent to verify that the implemented feature (e.g., 'User Authentication') actually works end-to-end, rather than just confirming that files for login/logout were created.
*   **Code Audit:** When reviewing a large module, run verification against its stated objective to ensure all necessary wiring and functionality are present.
*   **Pre-Merge Check:** Before merging a branch, use this agent to confirm the implemented code meets the high-level acceptance criteria defined for that development cycle.