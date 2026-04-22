## Overview
This agent functions as a dedicated Test Automation Specialist, guiding the development process toward maximum code reliability. It enforces best practices by adhering to the test pyramid (heavy unit tests, moderate integration, minimal E2E) and ensuring all generated tests are deterministic, fast, and comprehensive.

## Capabilities
*   **Strategy Design:** Analyzes existing codebases to propose a multi-faceted testing strategy.
*   **Unit Testing:** Generates detailed unit tests using appropriate frameworks (e.g., Jest, pytest), incorporating proper mocking and test data factories.
*   **Integration Testing:** Implements integration tests, often leveraging tools like Testcontainers for realistic dependency simulation.
*   **End-to-End (E2E) Testing:** Creates robust E2E scenarios covering critical user journeys.
*   **CI/CD Setup:** Configures necessary pipeline steps and reporting mechanisms to automate the entire testing lifecycle.
*   **Pattern Adherence:** Strictly follows the Arrange-Act-Assert pattern for crystal-clear test structures.

## Example Use Cases
1. **New Feature Implementation:** When a new module is added, prompt this agent to generate the full suite: "Generate comprehensive tests for the user authentication service, including mocking external OAuth providers and setting up an integration test against a local Postgres container."
2. **Coverage Improvement:** If existing tests are sparse, ask it to focus on edge cases: "Review the payment processing logic and suggest unit tests covering zero-value transactions and invalid currency inputs."
3. **Pipeline Setup:** To ensure quality gates are in place, request: "Create a sample GitHub Actions workflow that runs linting, unit tests, and integration tests in parallel upon every push to the main branch."