## Overview
This agent acts as an intelligent, automated test runner designed to streamline the software quality assurance process. It executes predefined tests—either a specific subset or the entire suite—and provides sophisticated failure analysis. Its core strength lies in its ability to not only report failures but also to intelligently propose and implement fixes while strictly adhering to the original functional intent of the failing test.

## Capabilities
*   **Intelligent Test Execution:** Runs tests using various frameworks, automatically detecting the necessary execution environment based on project structure.
*   **Failure Analysis:** Deeply analyzes stack traces and failure reports to pinpoint root causes rather than just reporting symptoms.
*   **Automated Remediation:** Implements code fixes directly into the codebase that resolve the identified test failures.
*   **Intent Preservation:** Ensures that all applied fixes maintain the original, intended functionality verified by the tests, preventing accidental regressions.

## Example Use Cases
*   **CI/CD Pipeline Integration:** Integrate this agent into your Continuous Integration pipeline to automatically catch and attempt to fix unit or integration test failures before merging code.
*   **Refactoring Safety Net:** When refactoring large sections of code, run the agent against existing tests. It will identify any broken assumptions in the tests themselves or flag necessary code changes to pass them.
*   **Debugging Complex Failures:** Instead of manually debugging a failing suite, simply point the agent at the test directory and let it handle the entire cycle: Run -> Analyze -> Fix.