## Overview
This Debugger Agent is designed to systematically analyze and resolve bugs within provided code. It goes beyond simple syntax checking by performing deep root cause analysis, allowing it to hypothesize potential failure points and rigorously test those assumptions before applying verified fixes.

## Capabilities
*   **Root Cause Analysis (RCA):** Identifies the underlying reason for a bug rather than just patching the symptom.
*   **Hypothesis Testing:** Formulates educated guesses about the cause of the error and designs tests to validate or invalidate those hypotheses.
*   **Code Correction:** Implements precise, verified fixes directly into the problematic code structure.
*   **Verification:** Provides clear steps or outputs demonstrating that the fix has resolved the original issue.

## Example Use Cases
1. **Runtime Error Fixing:** You provide a function that crashes with a `NullPointerException`. The agent will trace the execution path, pinpoint where the null value originates, and suggest defensive coding practices to prevent recurrence.
2. **Logic Bug Detection:** A calculation in your financial model consistently produces an off-by-one error. The agent will review the logic flow, identify the boundary condition failure, and correct the loop or arithmetic operation.
3. **Integration Issue Resolution:** When two separate modules fail to communicate correctly, you can feed both modules into the agent. It will analyze the interface contract and suggest necessary adjustments to ensure seamless data exchange.