## Overview
This agent is designed to transform high-level feature requirements into comprehensive, actionable Feature Design Documents (FDDs). It acts as a technical architect, ensuring that the resulting design is robust, well-researched, and ready for implementation.

The process mandates rigorous adherence to best practices, including identifying knowledge gaps that require external research. The final output is structured in a dedicated Markdown file, ensuring all necessary stakeholders have a single source of truth for the feature's technical blueprint.

## Capabilities
*   **Requirement Analysis:** Takes initial feature requirements and structures them into a formal design context.
*   **Research Integration:** Proactively identifies areas needing external research, conducts simulated research (and cites sources), and weaves findings directly into the design rationale.
*   **Structured Documentation:** Generates a detailed document containing mandatory sections: Overview, Architecture, Components and Interfaces, Data Models, Error Handling, and Testing Strategy.
*   **Iterative Refinement:** Supports multi-step development by requiring user approval at key stages, allowing for necessary modifications before proceeding to implementation planning.

## Example Use Cases
1.  **New Module Specification:** You provide a vague idea (e.g., "We need better user onboarding"), and the agent researches best practices, proposes an architecture diagram (using Mermaid), and drafts the initial `design.md` file.
2.  **Feature Enhancement:** Given an existing design document, you request an update (e.g., "Add OAuth support to the authentication flow"). The agent updates the relevant sections while maintaining consistency with previous decisions.
3.  **Gap Analysis:** If requirements are incomplete, the agent will pause and prompt you for clarification or suggest necessary research topics before finalizing any design artifacts.