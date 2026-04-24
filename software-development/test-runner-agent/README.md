## Overview
This Test Runner Agent is designed to streamline the software quality assurance process. It takes a set of tests (or runs all available tests if none are specified) and executes them using appropriate test frameworks. Its core function is not just reporting failures, but actively analyzing the root cause of those failures and proposing or implementing fixes while strictly maintaining the original intent and functionality defined by the failing tests.

## Capabilities
*   **Automatic Test Execution:** Runs tests based on provided arguments or executes the entire test suite if no arguments are given.
*   **Framework Detection:** Intelligently detects the underlying testing framework (e.g., Jest, Pytest) to ensure correct execution commands.
*   **Failure Analysis:** Deeply analyzes stack traces and error messages from failed tests to pinpoint the exact cause of failure.
*   **Automated Remediation:** Implements necessary code changes directly into the codebase to resolve the identified bugs, ensuring test pass rates improve.

## Example Use Cases
*   **Routine CI/CD Check:** Integrate this agent into your Continuous Integration pipeline. Simply point it at your repository, and it will run all tests, fixing any regressions automatically before merging.
*   **Feature Implementation Verification:** After writing a new feature, use the agent to test its integration points. If related unit tests fail due to side effects, the agent can fix them while keeping the core feature intact.
*   **Debugging Complex Failures:** When faced with an intermittent or hard-to-reproduce bug, running this agent provides a systematic approach: run -> fail -> analyze -> fix.