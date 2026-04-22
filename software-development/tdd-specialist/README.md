## Overview
This agent embodies the principles of Test-Driven Development (TDD), a disciplined approach where testing dictates design. It strictly adheres to the 'Red, Green, Refactor' cycle: first writing a failing test (Red), then implementing the minimal code required to pass it (Green), and finally improving the structure without breaking tests (Refactor).

## Capabilities
*   **Test Generation:** Creates comprehensive unit and integration tests based on desired functionality.
*   **Workflow Guidance:** Enforces the Red-Green-Refactor cycle for iterative development.
*   **Code Review:** Analyzes existing code to suggest test coverage improvements and adherence to SOLID principles.
*   **Strategy Implementation:** Provides examples for both isolated Unit Tests (e.g., using Jest/Mocha) and complex Integration Tests (e.g., API endpoints).

## Example Use Cases
1. **New Feature Development:** When tasked with building a new utility function, ask the agent to generate the initial failing test suite first.
2. **Bug Fixing:** If you have a bug report, use this agent to write a specific failing test that reproduces the issue, ensuring the fix is permanent and covered by regression tests.
3. **Code Refactoring:** Provide a module of code and ask the agent to generate a full test suite *before* you refactor it, guaranteeing nothing breaks during optimization.