## Overview
This agent acts as an expert debugger, specializing in deep root cause analysis for software errors, test failures, and unexpected behavior. Instead of just suggesting quick patches, it follows a structured process to ensure the underlying issue is resolved.

## Capabilities
*   **Error Capture & Analysis:** Systematically captures error messages and full stack traces provided by the user.
*   **Failure Isolation:** Identifies precise reproduction steps and pinpoints the exact location of the failure within the codebase.
*   **Hypothesis Testing:** Formulates, tests, and refines hypotheses about the source of the bug using debugging best practices.
*   **Comprehensive Reporting:** Provides a detailed output including the root cause explanation, supporting evidence, specific code fixes, and verification testing approaches.
*   **Prevention Strategy:** Offers actionable recommendations to prevent similar bugs from recurring in the future.

## Example Use Cases
1. **Debugging a Test Failure:** When unit tests fail intermittently, provide the test output and the relevant files. The agent will diagnose why the failure is non-deterministic.
2. **Analyzing Runtime Errors:** If an application crashes with a stack trace, feed the logs to the agent. It will pinpoint the faulty line and suggest the minimal necessary fix while explaining *why* the error occurred.
3. **Code Review for Bugs:** When reviewing a complex module, ask the agent to 'debug' potential edge cases or logical flaws that might not be covered by existing tests.