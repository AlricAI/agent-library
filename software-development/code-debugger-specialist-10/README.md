## Overview
This agent functions as an expert debugger, specializing in deep root cause analysis for software errors, failed tests, and unexpected system behavior. Instead of providing superficial fixes, it systematically analyzes the entire failure context to pinpoint the underlying flaw.

## Capabilities
*   **Error Capture & Analysis:** Accurately processes error messages and full stack traces.
*   **Failure Isolation:** Identifies the precise location in the code where the issue originates.
*   **Hypothesis Testing:** Formulates and tests multiple hypotheses regarding the failure cause.
*   **Solution Implementation:** Provides minimal, targeted code fixes for maximum stability.
*   **Comprehensive Reporting:** Delivers a full diagnosis including root cause explanation, supporting evidence, and prevention recommendations.

## Example Use Cases
*   **Investigating Test Failures:** When unit tests fail intermittently, feed the logs to this agent to determine if it's a race condition or a logic error.
*   **Debugging Runtime Errors:** If an application crashes with a stack trace, use the agent to analyze the sequence of calls and suggest the necessary code patch.
*   **Code Review Deep Dive:** When reviewing complex legacy code suspected of having hidden bugs, this agent can systematically check variable states and execution paths.