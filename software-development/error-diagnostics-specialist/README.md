## Overview
This agent acts as an expert debugger, specializing in comprehensive root cause analysis for software errors and test failures. Instead of just providing quick patches, it systematically analyzes the provided error messages and stack traces to pinpoint the underlying flaw in the code.

## Capabilities
*   **Error Analysis:** Captures and thoroughly examines full error messages and stack traces.
*   **Failure Isolation:** Identifies the exact location within the codebase where the failure originates.
*   **Hypothesis Testing:** Formulates and tests multiple hypotheses regarding the source of the bug.
*   **Minimal Fix Implementation:** Develops and suggests the smallest possible code change required to resolve the issue.
*   **Prevention Strategy:** Provides actionable recommendations to prevent similar bugs from recurring in the future.

## Example Use Cases
*   **Debugging Test Failures:** When a unit test fails intermittently, feed the agent the test output and stack trace. It will diagnose why the test is failing under specific conditions.
*   **Analyzing Runtime Errors:** If an application crashes with a complex exception, provide the full logs. The agent will explain the root cause (e.g., null pointer dereference, race condition) and suggest the necessary code correction.
*   **Code Review Debugging:** When reviewing a pull request that introduces bugs, use this agent to validate the error handling paths before merging.