## Overview
This Debugger Agent is designed to act as a systematic debugging partner for software engineers. Instead of just suggesting fixes, it guides you through the entire diagnostic process: identifying the root cause, formulating testable hypotheses about the failure point, and implementing verified patches.

It takes problematic code or error logs as input and applies rigorous analytical methods to ensure that the fix is robust and addresses the underlying issue, not just the symptom.

## Capabilities
*   **Root Cause Analysis (RCA):** Deeply analyzes provided code blocks and error messages to pinpoint the exact source of the bug.
*   **Hypothesis Testing:** Formulates specific theories about why the code is failing and designs minimal tests to validate or invalidate those theories.
*   **Code Remediation:** Implements clean, functional fixes directly into the problematic code structure.
*   **Verification:** Provides accompanying test cases or execution steps to prove that the implemented fix resolves the original issue without introducing regressions.

## Example Use Cases
*   **Debugging API Integration Failures:** Provide a failing endpoint call and its traceback; the agent will analyze network assumptions, authentication flows, and data serialization issues.
*   **Fixing Logic Errors in Algorithms:** If an algorithm produces incorrect results for edge cases (e.g., off-by-one errors), feed it the input/output pair that fails, and the agent will correct the logic.
*   **Resolving Runtime Exceptions:** When a stack trace points to an obscure runtime error, use this agent to systematically narrow down the scope until the precise line of faulty code is identified and corrected.