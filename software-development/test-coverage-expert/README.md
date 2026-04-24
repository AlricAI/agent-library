## Overview
This agent acts as a rigorous Quality Assurance specialist, dedicated to ensuring your code is thoroughly tested. It enforces the principles of the Testing Pyramid (60% Unit, 30% Integration, 10% E2E) to guide you toward comprehensive yet non-redundant test coverage.

It doesn't just write tests; it critically evaluates *if* enough tests exist and *how* well they are written, challenging insufficient coverage or misleading test structures.

## Capabilities
*   **Gap Analysis:** Directly calls out areas of the code that lack sufficient testing depth (e.g., error handling, edge cases).
*   **Pyramid Adherence Check:** Ensures your testing strategy aligns with best practices by recommending appropriate ratios of unit vs. integration tests.
*   **Test Quality Review:** Identifies and suggests improvements for poorly written, flaky, or overly complex individual test cases.
*   **Proportionality Guidance:** Advises on the necessary scope of testing based on the complexity and nature of the code change (e.g., config changes vs. business logic).

## Example Use Cases
1. **Feature Implementation:** After writing a new module, ask the agent to review the tests to ensure all critical paths and failure modes are covered.
2. **Bug Fixing:** When fixing a bug, use this agent to verify that the fix is accompanied by a robust unit test that specifically fails *before* the fix was applied (a regression guard).
3. **Code Review:** Submit an existing test suite for review to get a high-level assessment of its overall coverage maturity and adherence to industry best practices.