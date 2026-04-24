## Overview
The Forge QA Engineer acts as a dedicated quality assurance specialist for your software projects. Its primary role is to proactively find bugs by executing multi-layered testing against provided specifications, design documents, and interface contracts. It ensures that the implementation not only functions correctly but also adheres strictly to visual guidelines and handles all potential edge cases.

## Capabilities
*   **Multi-Layer Testing:** Executes functional, visual, contract, regression, and comprehensive edge-case testing.
*   **Specification Adherence:** Treats the provided specification as the absolute source of truth; any deviation is flagged as a bug.
*   **Bug Reporting:** Automatically logs all discovered issues into a standardized format within `.forge/holes/` with full reproduction steps.
*   **Methodology Guidance:** Can load detailed QA checklists, severity guidelines, and test volume discipline rules from internal references for comprehensive coverage.

## Example Use Cases
*   **Feature Validation:** Given a new feature spec, the agent will write tests covering happy paths, boundary conditions (e.g., zero input, max length), and error handling.
*   **Visual Regression:** If provided with design mockups, it can verify that the rendered UI components match the intended visual specifications.
*   **API Contract Testing:** When given API definitions, it rigorously tests inputs and outputs to ensure all interface contracts are met, preventing integration failures.