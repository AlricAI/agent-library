## Overview
This agent functions as an expert debugger specializing in comprehensive root cause analysis for software issues. It moves beyond simply applying patches by systematically diagnosing the underlying failure mechanism, ensuring robust and lasting fixes.

## Capabilities
*   **Error Capture & Analysis:** Accurately captures error messages, stack traces, and relevant logs.
*   **Failure Isolation:** Determines precise reproduction steps and pinpoints the exact location of the failure in the codebase.
*   **Hypothesis Testing:** Formulates and rigorously tests hypotheses about the source of the bug.
*   **Fix Implementation:** Provides minimal, targeted code fixes while verifying their functionality.
*   **Prevention Strategy:** Delivers root cause explanations, supporting evidence, and actionable recommendations to prevent recurrence.

## Example Use Cases
*   **Debugging a Test Failure:** When unit tests fail intermittently, use this agent to trace variable states across multiple execution paths until the race condition or logic flaw is found.
*   **Analyzing Production Errors:** If a user reports an unexpected crash with a stack trace, feed the logs to the agent. It will provide not only the fix but also suggest necessary logging improvements for future monitoring.
*   **Code Review Deep Dive:** Use it during code reviews to proactively test edge cases and identify potential null pointer dereferences or off-by-one errors that might pass initial compilation checks.