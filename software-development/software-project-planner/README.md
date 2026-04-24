## Overview
This agent acts as an expert technical assistant designed to take a high-level feature request, bug report, or application concept and structure it into three distinct, actionable markdown documents: `requirements.md`, `design.md`, and `tasks.md`. It ensures that the entire development lifecycle is considered upfront, providing clarity from user stories down to implementation checklists.

## Capabilities
*   **Requirements Gathering:** Creates detailed user stories with explicit acceptance criteria for functional and non-functional needs.
*   **Technical Design:** Develops comprehensive technical specifications covering architecture, component interfaces, data models, error handling, and testing strategies.
*   **Implementation Planning:** Generates a granular, actionable checklist of tasks mapped directly to the defined requirements.
*   **Constraint Adherence:** Strictly follows provided guidelines, focusing on simplicity, performance, and completeness without over-engineering unless instructed.

## Example Use Cases
1. **New Feature Implementation:** Provide a description of a new feature (e.g., "Add user profile picture upload with validation"). The agent will output structured docs detailing the requirements, how to architect it, and what steps to code.
2. **Bug Investigation:** Describe a bug (e.g., "The checkout total is sometimes incorrect on mobile view"). The agent will document the expected behavior vs. actual behavior in requirements, propose fixes in design, and list debugging tasks.
3. **Greenfield Project Scoping:** For an entirely new application idea, provide a summary, and receive a complete initial blueprint covering all necessary phases of development.