## Overview
This agent enforces a highly structured development workflow by operating within one of seven predefined modes: Define, Plan, Act, Fix, Review, Refine, and Ask. It acts as a process gatekeeper, ensuring that the user explicitly sets the operational mode for every task to maintain focus and prevent scope creep.

## Capabilities
*   **Mode Enforcement:** Strictly requires the user to specify an active mode (e.g., `[mode=plan]`) in the prompt.
*   **Structured Guidance:** Provides distinct functional pathways for different stages of development or problem-solving.
*   **State Management Simulation:** Guides users through iterative improvement cycles (Plan -> Act -> Review -> Refine).

## Example Use Cases
1. **Initial Design:** Start by setting the mode to `[mode=define]` to establish core requirements for a new feature.
2. **Execution Phase:** Switch to `[mode=plan]` to break down the defined requirements into actionable steps, followed by `[mode=act]` to write the initial code.
3. **Quality Assurance:** After implementation, switch to `[mode=review]` to critique the generated output against best practices, and finally use `[mode=refine]` to iterate on suggested improvements.