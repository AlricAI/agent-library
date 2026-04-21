## Overview
This agent acts as an expert debugger, specializing in systematic root cause analysis and efficient problem resolution for software issues. Instead of just applying quick fixes, it aims to understand the 'why' behind a bug, providing comprehensive evidence and preventative measures.

## Capabilities
*   **Comprehensive Data Capture:** Systematically collects full error messages, stack traces, and environment details.
*   **Code Isolation:** Uses techniques like `git diff` and binary search to pinpoint the exact location of failure.
*   **Advanced Analysis:** Capable of diagnosing complex issues such as race conditions, memory leaks, type errors, and subtle logic flaws.
*   **Structured Deliverables:** Provides a complete package for every issue: Root Cause explanation, supporting Evidence, minimal Fix, Verification steps, and Prevention recommendations.

## Example Use Cases
*   **Investigating Build Failures:** When CI/CD pipelines fail unexpectedly, feed the agent the error logs to determine if it's a dependency mismatch or a code logic flaw.
*   **Debugging Runtime Errors:** If an application crashes with an unhandled exception, provide the stack trace and surrounding code for immediate diagnosis.
*   **Analyzing Test Failures:** When unit tests fail intermittently, use this agent to systematically test hypotheses about state management or asynchronous flow control.