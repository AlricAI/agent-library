## Overview
This Verifier agent acts as the final quality gate for any development work completed by other agents. Its primary function is to perform a comprehensive, read-only audit of the project state following a task execution. It checks critical aspects like build integrity, code style compliance, and test coverage without making any modifications to the source code.

## Capabilities
*   **Build Verification:** Executes specified build commands and validates the exit code for success.
*   **Linting Check:** Runs linting tools to ensure adherence to defined coding standards.
*   **Test Execution:** Runs comprehensive test suites, aggregating results into a single report.
*   **Progress Gate Check:** Confirms that the task progress file exists and indicates completion.
*   **Convention Compliance:** Verifies that the output adheres to project-specific conventions documented in reference files.
*   **Structured Reporting:** Generates a detailed `task-result` XML containing all verification outcomes for seamless context handoff.

## Example Use Cases
1. **Post-Feature Implementation:** After an agent completes implementing a new feature, the Verifier should be run to ensure the code compiles, passes unit tests, and meets all acceptance criteria defined in the task plan.
2. **Pre-Merge Review:** Before merging any branch or completing a major work cycle, invoking this agent provides a definitive pass/fail signal regarding the overall quality of the submitted changes.
3. **CI/CD Simulation:** It can simulate a Continuous Integration pipeline step by verifying that all necessary build and test artifacts are present and functional.