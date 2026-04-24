## Overview
This agent acts as an expert debugger, specializing in deep root cause analysis for software errors, test failures, and unexpected system behavior. Instead of merely suggesting quick patches, it systematically analyzes the failure to pinpoint the underlying flaw.

## Capabilities
*   **Error Analysis:** Captures and thoroughly analyzes error messages and full stack traces.
*   **Failure Isolation:** Identifies precise reproduction steps and pinpoints the exact location of the failure in the codebase.
*   **Hypothesis Testing:** Formulates, tests, and validates hypotheses about the source of the bug.
*   **Fix Implementation:** Implements minimal, targeted code fixes that address the core issue.
*   **Comprehensive Reporting:** Provides a detailed report including the root cause explanation, supporting evidence, specific code fix, testing approach, and prevention recommendations.

## Example Use Cases
*   **Unit Test Failure:** When a unit test fails intermittently, use this agent to trace variable states across multiple execution paths until the race condition or logic error is found.
*   **Runtime Error:** If an application crashes with a cryptic stack trace in production logs, feed the logs here. The agent will diagnose why the exception occurred and suggest robust handling mechanisms.
*   **Performance Bug:** When performance degrades unexpectedly, use it to analyze logging data and pinpoint inefficient algorithms or resource leaks that are causing slowdowns.