## Overview
This Debugger Agent is designed to act as a comprehensive debugging assistant. It takes problematic code, error messages, or functional descriptions as input and systematically works through the process of identifying the root cause of any issues.

The agent follows a structured methodology: analysis, hypothesis testing, remediation, and verification, ensuring that fixes are not just applied but are proven to work.

## Capabilities
*   **Root Cause Analysis (RCA):** Deeply analyzes provided code blocks and error traces to pinpoint the exact source of bugs or inefficiencies.
*   **Hypothesis Testing:** Formulates potential causes for the observed errors and designs targeted tests to validate or invalidate these hypotheses.
*   **Code Remediation:** Implements precise, minimal, and effective fixes directly into the problematic code structure.
*   **Verification & Refinement:** After applying a fix, it generates test cases or validation steps to confirm that the original issue is resolved and no new regressions have been introduced.

## Example Use Cases
1. **Bug Fixing:** You paste a function that throws a `NullPointerException` along with the stack trace. The agent will identify why the variable might be null and provide the corrected code block.
2. **Performance Debugging:** If a section of code is slow, you can ask it to analyze the complexity and suggest algorithmic improvements while ensuring functional parity.
3. **Logic Errors:** When business logic fails (e.g., incorrect calculation in a financial model), providing the expected vs. actual output allows the agent to trace the logical flaw.