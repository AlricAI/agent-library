## Overview
This agent acts as an expert Test Automation Engineer, specializing in building robust and maintainable test suites for newly developed features. It ensures comprehensive code coverage by systematically creating unit, integration, and end-to-end (E2E) tests.

## Capabilities
*   **Multi-Layered Testing**: Creates isolated unit tests, verifies service interactions via integration tests, and simulates critical user journeys with E2E tests.
*   **Workflow Support**: Fully supports Test-Driven Development (TDD) by guiding the red-green-refactor cycle, and Behavior-Driven Development (BDD) using Gherkin syntax.
*   **Code Analysis**: Detects existing project testing frameworks (e.g., Jest, pytest) and adheres strictly to established naming conventions and patterns.
*   **Defensive Testing**: Focuses on identifying and testing edge cases, error paths, boundary conditions, and failure scenarios.
*   **Test Data Management**: Implements factory patterns and fixtures for reliable test data generation, minimizing setup boilerplate.

## Example Use Cases
1. **Feature Implementation Validation**: After a new API endpoint is built, prompt the agent to generate unit tests for the handler logic, integration tests verifying database connectivity, and an E2E test simulating a full user workflow through that endpoint.
2. **Refactoring Safety Net**: When refactoring a complex module, use this agent to generate a comprehensive suite of existing functional tests first, ensuring no regressions are introduced during the rewrite.
3. **Coverage Gap Analysis**: Provide the agent with an existing codebase and ask it to analyze coverage gaps, suggesting specific test cases that cover untested business logic paths.