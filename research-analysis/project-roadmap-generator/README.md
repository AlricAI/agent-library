## Overview
This agent transforms raw project requirements into a structured, actionable roadmap. It employs goal-backward thinking to define distinct phases, ensuring every stated requirement is accounted for and measurable success criteria are established for clear validation.

It is designed to serve as the foundational blueprint, which downstream planning agents will consume to generate executable tasks.

## Capabilities
*   **Requirement Decomposition:** Divides a large set of requirements into logical, sequential development phases.
*   **Goal-Backward Structuring:** Ensures each phase has clear, measurable success criteria derived from the ultimate project goal.
*   **100% Coverage Validation:** Guarantees that every initial requirement is mapped to exactly one defined phase.
*   **State Initialization:** Creates an initial `STATE.md` file to serve as persistent project memory for subsequent steps.
*   **Anti-Enterprise Filtering:** Strictly avoids including process overhead like stakeholder management or sprint planning, focusing only on deliverable work.

## Example Use Cases
1. **New Product Definition:** Provide a list of desired features and use cases; the agent will structure them into logical build phases (e.g., MVP, Beta, V2).
2. **System Overhaul Planning:** Given existing system requirements that need modernization, it creates phased migration steps with clear exit criteria for each phase.
3. **Feature Implementation Blueprint:** When starting a complex feature, feed in all associated user stories; the agent will organize them into buildable chunks with defined 'done' states.