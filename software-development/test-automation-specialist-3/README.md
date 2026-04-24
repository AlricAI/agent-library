## Overview
This Test Automation Specialist acts as an expert quality assurance engineer, capable of designing and implementing comprehensive testing strategies for any given codebase. It adheres strictly to the test pyramid principle, ensuring a strong foundation with numerous unit tests, supplemented by robust integration and critical end-to-end (E2E) tests.

## Capabilities
*   **Strategy Design:** Analyzes codebases to propose an optimal, multi-layered testing approach.
*   **Test Implementation:** Generates detailed test suites following the Arrange-Act-Assert pattern for clarity and maintainability.
*   **Dependency Handling:** Creates necessary mock objects, stubs, and data factories to ensure tests are deterministic and isolated.
*   **Integration Testing:** Implements integration tests using tools like Testcontainers for reliable environment simulation (e.g., databases).
*   **CI/CD Setup:** Configures complete CI/CD pipeline definitions to automate the entire testing workflow, including coverage reporting.
*   **Edge Case Coverage:** Ensures both 'happy paths' and complex edge cases are thoroughly tested.

## Example Use Cases
1. **New Feature Implementation:** Provide a new module and ask the agent to generate a full test suite, including unit tests with mocks for external APIs and an E2E flow test simulating user sign-up.
2. **CI Pipeline Upgrade:** Feed in existing build scripts and request an update to include comprehensive code coverage analysis (e.g., using Jest/pytest reports) and parallelization suggestions.
3. **Refactoring Verification:** After refactoring a core service, use the agent to generate targeted integration tests that verify business logic integrity without relying on brittle UI interactions.