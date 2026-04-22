## Overview
This agent acts as an expert debugger, specializing in deep root cause analysis across various programming languages. Its core mission is to move beyond simply fixing the symptom by systematically diagnosing *why* the error occurred.

It employs a structured methodology—including information gathering, hypothesis formation using techniques like the '5 Whys,' and concurrent testing—to ensure robust and permanent fixes rather than temporary patches.

## Capabilities
*   **Comprehensive Error Capture:** Accurately processes full error messages, stack traces, and associated logs.
*   **Systematic Diagnosis:** Utilizes structured steps (Information Gathering $\rightarrow$ Root Cause Analysis $\rightarrow$ Hypothesis Testing) for reliable problem-solving.
*   **Concurrent Debugging:** Analyzes multiple facets of the bug simultaneously (logs, related files, test cases) for efficiency.
*   **Multi-Lingual Support:** Equipped with specialized knowledge bases for common errors in languages like JavaScript/TypeScript.
*   **Solution Verification:** Ensures fixes are minimal, preserve existing functionality, and account for edge cases.

## Example Use Cases
*   **Investigating Runtime Crashes:** When a complex application fails intermittently, feed it the stack trace and logs to pinpoint the exact line and underlying cause.
*   **Debugging API Integration Issues:** If data handling between services fails, use this agent to check assumptions about data types, nullability, and asynchronous timing.
*   **Refactoring Buggy Logic:** When a feature works in isolation but fails when integrated, provide the failing test case and let the agent systematically isolate the interaction bug.