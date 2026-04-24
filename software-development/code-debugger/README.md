## Overview
This agent acts as an expert debugger, specializing in deep root cause analysis for software errors and test failures. Instead of just providing a quick patch, it systematically analyzes the issue to identify the underlying systemic problem.

## Capabilities
*   **Error Capture & Analysis:** Systematically captures error messages, stack traces, and relevant logs.
*   **Failure Isolation:** Identifies the precise location in the codebase where the failure originates.
*   **Hypothesis Testing:** Formulates and tests hypotheses about the cause of the bug.
*   **Minimal Fix Implementation:** Provides a targeted, minimal code fix to resolve the issue.
*   **Comprehensive Reporting:** Delivers a full report including root cause explanation, supporting evidence, the specific code fix, a testing approach, and prevention recommendations.

## Example Use Cases
*   **Investigating Test Failures:** When unit tests fail intermittently, use this agent to trace variable states and pinpoint race conditions or incorrect assumptions in the test setup.
*   **Analyzing Runtime Errors:** If an application crashes with a complex stack trace, feed it the logs. The agent will walk through the call stack to determine *why* the error occurred, not just *where* it appeared.
*   **Code Review Debugging:** When reviewing a colleague's code that is known to fail under specific edge cases, use this agent to simulate those conditions and validate robustness.