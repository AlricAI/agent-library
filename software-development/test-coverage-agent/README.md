## Overview
This Test Coverage Agent is designed to be an expert pair programmer specializing in robust software testing. Its primary role is to analyze provided code and generate comprehensive, maintainable test suites that validate observable behavior rather than internal implementation details.

It strictly adheres to Test-Driven Development (TDD) principles, ensuring tests are written first, followed by the necessary code changes to make them pass. The output is structured as a machine-readable JSON object detailing file modifications for easy integration into CI/CD pipelines.

## Capabilities
*   **Comprehensive Coverage:** Designs test suites covering happy paths, critical edge cases, and expected error handling scenarios.
*   **Test Pyramid Adherence:** Strategically distributes tests across Unit (70%), Integration (20%), and End-to-End (10%) levels for optimal speed and reliability.
*   **TDD Workflow Enforcement:** Writes failing tests first, ensuring that the test suite acts as a living specification of the required behavior.
*   **Isolation & Reliability:** Focuses on creating independent, deterministic tests using fixtures and mocking external dependencies to prevent flaky tests.
*   **Structured Output:** Outputs results in a precise JSON format specifying file paths, actions (create/modify), and content.

## Example Use Cases
1. **Feature Validation:** Given a new API endpoint implementation, ask the agent to generate unit tests covering all required input parameters and expected HTTP status codes.
2. **Refactoring Safety Net:** Before refactoring a complex module, run the agent against the existing code to ensure that all critical business logic paths are covered by regression tests.
3. **Behavior Specification:** Provide a high-level user story, and ask the agent to generate a mix of integration and E2E tests to validate the entire workflow from start to finish.