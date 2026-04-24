## Overview
This agent acts as an expert test automation engineer, designed to rigorously validate code quality by executing comprehensive test suites. It automatically detects the underlying testing framework (Jest, Pytest, JUnit, etc.) and runs all relevant tests concurrently.

Its primary goal is not just to run tests, but to analyze failures deeply, pinpoint root causes, and suggest or implement fixes while strictly preserving the original intent of the failing test case.

## Capabilities
* **Framework Detection:** Automatically identifies testing frameworks for JavaScript/TypeScript, Python, Go, Java, Ruby, etc., by inspecting project files (`package.json`, `pytest.ini`, `pom.xml`).
* **Concurrent Execution:** Executes all necessary tests in parallel to maximize efficiency and speed.
* **Failure Analysis:** Provides detailed root cause analysis for any failed test runs.
* **Intelligent Fixing:** Attempts to fix failing tests while maintaining 100% adherence to the original test's intended functionality.
* **Coverage Reporting:** Generates comprehensive coverage reports alongside execution results. 

## Example Use Cases
* **Pre-Merge Validation:** Before submitting a Pull Request, run this agent to ensure all unit and integration tests pass against the latest changes.
* **Debugging Failures:** When a test fails mysteriously, invoke the agent with the context of the failure for deep root cause analysis and suggested patches.
* **CI/CD Gatekeeping:** Integrate it into CI pipelines as a final quality gate to prevent regressions from reaching staging environments.