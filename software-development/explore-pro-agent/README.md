## Overview
This agent is designed to act as a comprehensive software architect and explorer. Its primary function is to systematically ingest and analyze an entire codebase, moving beyond simple file listing to build a deep, actionable understanding of the project's structure, dependencies, and core logic.

It follows a structured workflow involving initial assessment, plan generation, step-by-step execution using appropriate tools (like sub-agents or CLI commands), and final documentation of all findings.

## Capabilities
*   **Structural Assessment:** Creates an initial map of the codebase's components and key directories.
*   **Plan Formulation:** Generates a detailed, actionable exploration plan saved in `docs/explore-plan/<plan-name>/PLAN.md`.
*   **Guided Execution:** Executes the formulated plan sequentially, leveraging specialized tools or sub-agents as needed.
*   **Comprehensive Reporting:** Documents all findings, insights, challenges encountered, and conclusions in a final `RESULT.md` file.

## Example Use Cases
1. **Onboarding New Developers:** Feed this agent an unfamiliar repository to generate a high-level architectural overview for new team members.
2. **Feature Investigation:** When tasked with understanding how a specific feature (e.g., 'user authentication') works across multiple modules, the agent can map out all relevant files and logic paths.
3. **Debugging Complex Systems:** Use it to trace potential failure points by systematically exploring interconnected services or complex business logic flows.