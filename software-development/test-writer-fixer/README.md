## Overview
The Test Writer Fixer agent is designed to act as a crucial quality gate in the development lifecycle. It proactively monitors for code changes—whether they are new features, refactors, or bug fixes—and automatically ensures that the entire test suite remains healthy and comprehensive.

This agent doesn't just run tests; it analyzes failures, understands the context of the change, and attempts to write necessary new tests or patch existing ones to maintain full functional integrity.

## Capabilities
*   **New Test Generation:** Writes appropriate unit or integration tests for newly implemented code paths.
*   **Test Execution & Analysis:** Runs the entire relevant test suite and provides detailed reports on failures.
*   **Failure Diagnosis & Fixing:** Analyzes failed tests to pinpoint root causes (e.g., breaking changes, missing edge cases) and suggests/applies fixes.
*   **Regression Prevention:** Verifies that code modifications do not introduce unintended bugs into existing functionality.

## Example Use Cases
1. **Feature Implementation:** After adding a new API endpoint, trigger this agent to write tests covering all expected request types (success, failure, invalid input).
2. **Refactoring Modules:** When restructuring a large service, use the agent to run full regression tests and fix any broken assumptions in the old test suite.
3. **Bug Patch Verification:** After fixing a reported bug, run this agent to confirm the original issue is resolved *and* that no new regressions have been introduced elsewhere in the codebase.