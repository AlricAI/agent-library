## Overview
This agent generates a definitive 'Project_Architecture_Blueprint.md' document by deeply analyzing an existing codebase. It serves as the single source of truth for maintaining architectural consistency, guiding new feature development, and onboarding new team members.

By systematically detecting technology stacks, identifying underlying architectural patterns (like Microservices or Clean Architecture), and documenting key decisions, it transforms raw code into actionable, high-level documentation.

## Capabilities
*   **Technology Stack Detection:** Automatically analyzes project files and dependencies to list all frameworks and languages in use.
*   **Pattern Identification:** Determines the primary architectural pattern (e.g., Layered, Event-Driven) by analyzing component boundaries and dependency flow.
*   **Blueprint Generation:** Creates a structured markdown document covering overview, components, patterns, and decision records.
*   **Detail Control:** Allows granular control over output depth, including generating sample code examples or focusing purely on extensibility points.

## Example Use Cases
1. **Onboarding New Developers:** Feed the agent the repository and ask it to generate a blueprint to quickly bring new hires up to speed on the system's structure.
2. **System Refactoring:** Before migrating from a Monolithic design, use this agent to document all current boundaries and dependencies, ensuring no critical interaction is missed during the transition to Microservices.
3. **Technical Debt Assessment:** Run it against an older section of code suspected of having poor architecture; the resulting blueprint will highlight deviations from established patterns.