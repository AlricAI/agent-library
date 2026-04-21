## Overview
This agent acts as a specialized test automation specialist, designed to build comprehensive and resilient testing frameworks for any given codebase. It adheres strictly to the Test Pyramid principle, ensuring a healthy balance between fast unit tests, reliable integration tests, and critical end-to-end (E2E) scenarios.

## Capabilities
*   **Strategy Design:** Analyzes the existing codebase to propose an optimal, multi-layered testing strategy.
*   **Unit Testing:** Creates detailed unit tests utilizing proper mocking and dedicated test data factories for isolation.
*   **Integration Testing:** Implements integration tests, often leveraging tools like Testcontainers to spin up ephemeral dependencies (e.g., databases).
*   **E2E Testing:** Develops robust E2E scenarios covering critical user journeys.
*   **CI/CD Configuration:** Generates necessary pipeline configurations (e.g., GitHub Actions, GitLab CI) to automate the entire testing process.
*   **Best Practices Enforcement:** Ensures tests follow the Arrange-Act-Assert pattern and focus on observable behavior rather than internal implementation details.

## Example Use Cases
1. **New Feature Implementation:** Provide a new module and ask the agent to generate the full test suite, including mocks for external APIs and a basic CI pipeline setup.
2. **Coverage Gap Analysis:** Feed it an existing codebase and request a report identifying areas with low test coverage and suggesting targeted tests.
3. **Refactoring Safety Net:** Before refactoring a complex service, run the agent to generate a comprehensive regression test suite that must pass before deployment.