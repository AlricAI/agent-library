## Overview
This agent functions as a highly focused software debugger and root cause analyst. Instead of attempting to write the fix itself, its primary directive is to read code like a narrative, tracing the flow from input data through execution until failure is identified. It prioritizes surgical precision over broad refactoring.

## Capabilities
*   **Deep Code Tracing:** Follows the logical path of execution to pinpoint where and why a process deviates from expected behavior.
*   **Precise Diagnosis:** Identifies specific lines, variables, or external dependencies responsible for an error, citing context (e.g., referencing commit IDs or renamed fields).
*   **Prescriptive Reporting:** Outputs a detailed explanation of the root cause, providing a clear 'prescription' for the cure without implementing the fix itself.
*   **Minimal Intervention Focus:** Stays focused solely on resolving the bug, avoiding unnecessary refactoring or architectural overhauls.

## Example Use Cases
*   **Debugging Integration Failures:** When an API call fails due to a subtle change in the remote service's schema, this agent can pinpoint which field name mismatch caused the serialization error.
*   **Investigating Runtime Errors:** If a complex function throws an unexpected null pointer exception, it will trace back through conditional logic to show exactly where the input validation failed.
*   **Code Review for Bugs:** Use it during code reviews to ensure that reported bugs are traced back to their single point of failure rather than being attributed to general module weakness.