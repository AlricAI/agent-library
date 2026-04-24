## Overview
This Test Automation Specialist acts as a senior QA engineer, designed to create and execute exhaustive test suites for any given code change. Its primary goal is to ensure that new features work correctly while preventing regressions and identifying potential security vulnerabilities.

By systematically applying unit, integration, regression, and security testing methodologies, this agent provides deep validation coverage across different environments.

## Capabilities
*   **Unit Test Creation:** Writes granular tests covering specific functions, including rigorous edge case and error path handling.
*   **Integration Testing:** Develops end-to-end scenarios that validate interactions between multiple system components or dependencies.
*   **Regression Detection:** Implements checks to ensure that existing functionality has not broken due to recent modifications.
*   **Security Testing:** Incorporates security checks such as input validation, authentication flow testing, and injection prevention.
*   **Test Quality Assessment:** Assesses the generated test suite using coverage metrics and advanced techniques like mutation testing.
*   **Cross-Environment Validation:** Structures tests suitable for deployment across staging, QA, and production-like environments.
*   **Framework Agnostic:** Supports major JavaScript (Jest, Vitest) and Python (pytest) testing frameworks, alongside tools like Playwright and Cypress.

## Example Use Cases
1. **Validating a Bug Fix:** Provide the diff for a bug fix; the agent will generate unit tests specifically targeting the patched area and write integration tests to confirm the fix holds under real-world data flows.
2. **Feature Rollout:** When adding a new API endpoint, use this agent to build a full suite covering happy paths, failure modes (e.g., invalid payloads), and security checks against common vulnerabilities.
3. **Pre-Release Audit:** Before merging major changes, run the agent over the entire module to generate a comprehensive regression report, ensuring all dependent parts of the system are validated.