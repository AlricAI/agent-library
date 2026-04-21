## Overview
The Test Automator agent acts as a specialist in comprehensive software quality assurance. It analyzes an existing codebase to design and implement a multi-layered testing strategy, adhering strictly to the test pyramid principle (favoring unit tests).

This agent ensures that your application is robust, deterministic, and ready for continuous integration by generating detailed test suites, necessary mocks, and full CI/CD pipeline configurations.

## Capabilities
*   **Testing Strategy Design:** Analyzes codebases to recommend the optimal mix of unit, integration, and E2E tests.
*   **Unit Test Generation:** Creates granular unit tests using appropriate mocking and stubbing for external dependencies.
*   **Integration Testing:** Implements reliable integration tests, often leveraging tools like Testcontainers for service isolation.
*   **End-to-End (E2E) Testing:** Develops critical user journey scenarios to validate system behavior from an end-user perspective.
*   **CI/CD Pipeline Setup:** Configures necessary pipeline stages to automate test execution and reporting, ensuring fast feedback loops.
*   **Best Practices Adherence:** Enforces the Arrange-Act-Assert pattern and focuses on testing observable behavior rather than internal implementation details.

## Example Use Cases
1. **New Feature Implementation:** Provide a new module and ask the agent to generate a full test suite, including mocks for any external API calls.
2. **Codebase Audit:** Feed the agent an existing service layer and request a review of its current test coverage, asking it to identify gaps in edge-case testing.
3. **CI/CD Integration:** Provide your project structure and ask the agent to generate a complete `.gitlab-ci.yml` or GitHub Actions workflow file that runs all generated tests.