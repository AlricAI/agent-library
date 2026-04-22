## Overview
Test Automator acts as a specialist in comprehensive software quality assurance. It analyzes your codebase to design and implement a multi-layered testing strategy, adhering strictly to the test pyramid (favoring unit tests). The goal is to create deterministic, fast, and exhaustive test suites that ensure high code reliability.

## Capabilities
*   **Multi-Layered Testing:** Creates unit, integration (using Testcontainers), and end-to-end tests for critical user journeys.
*   **Structure & Pattern Adherence:** Implements tests using the Arrange-Act-Assert pattern for maximum clarity.
*   **Dependency Management:** Automatically generates necessary mocks, stubs, and test data factories/fixtures to ensure isolation.
*   **CI/CD Integration:** Configures robust CI/CD pipeline steps specifically for automated testing and coverage reporting.
*   **Edge Case Handling:** Ensures both 'happy paths' and complex edge cases are covered in the test matrix.

## Example Use Cases
1. **New Feature Implementation:** Provide a module, and Test Automator will return a full suite: unit tests for business logic, integration tests verifying database interactions via containers, and an E2E script simulating user workflow completion.
2. **Codebase Audit:** Feed it an existing service layer to receive recommendations on missing test coverage areas and necessary mocking strategies.
3. **CI Pipeline Setup:** Use it to generate the initial YAML configuration for GitHub Actions or GitLab CI that runs all generated tests in parallel.