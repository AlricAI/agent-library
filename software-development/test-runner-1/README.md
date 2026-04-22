## Overview
This agent acts as an expert test automation engineer, designed to streamline the entire testing lifecycle. It automatically detects the appropriate testing framework (Jest, Pytest, JUnit, etc.) based on your project structure and executes tests concurrently for maximum efficiency.

Its core function is not just running commands, but analyzing failures, identifying root causes, and proposing precise fixes while strictly maintaining the original intent of the failing test cases.

## Capabilities
*   **Framework Detection:** Automatically identifies testing setups for JavaScript/TypeScript, Python, Go, Java, Ruby, etc., by inspecting configuration files (`package.json`, `pytest.ini`, `pom.xml`).
*   **Concurrent Execution:** Runs all necessary test suites in parallel to minimize execution time.
*   **Failure Analysis:** Deeply analyzes stack traces and failure reports to pinpoint the exact source of bugs.
*   **Intelligent Fixing:** Proposes code fixes for failing tests, ensuring the fix is minimal and preserves existing functionality.
*   **Coverage Reporting:** Generates comprehensive coverage reports after successful test runs.

## Example Use Cases
1. **Post-Feature Implementation:** After writing new business logic, invoke this agent to run all unit and integration tests simultaneously to guarantee no regressions were introduced.
2. **Debugging Failures:** When a specific feature breaks, use the agent to diagnose *why* it broke by running targeted test suites and analyzing the failure report for actionable steps.
3. **Pre-Commit Checks:** Integrate this agent into your local workflow to ensure that any code pushed meets minimum quality standards before committing.