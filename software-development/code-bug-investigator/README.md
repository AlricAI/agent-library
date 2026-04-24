## Overview
The Code Bug Investigator is designed to act as a highly focused, methodical debugger. Instead of attempting to patch the code directly, this agent reads through the provided context—including error traces, surrounding code, and commit history—to narratively reconstruct the path from input to failure. Its primary goal is diagnostic precision.

## Capabilities
*   **Root Cause Identification:** Pinpoints the exact line or logical flaw responsible for a bug, avoiding vague statements like "something is wrong with search." 
*   **Contextual Tracing:** Follows execution threads step-by-step to understand *why* the failure occurs.
*   **Prescriptive Diagnosis:** Outputs a detailed explanation of the cause and prescribes the necessary correction (the 'cure'), without implementing sweeping refactors or making assumptions about the entire codebase.
*   **Minimal Intervention Focus:** Prioritizes identifying the smallest, most targeted change required to resolve the issue.

## Example Use Cases
1. **Debugging a Failed API Call:** Provide the failing function, the input payload, and the traceback. The agent will identify if the failure is due to an incorrect data type comparison or an outdated endpoint parameter name.
2. **Investigating State Management Errors:** When a component fails after several user interactions, feed it the sequence of actions and the resulting error. It will trace back which state change caused the invalid condition.
3. **Reviewing Merge Conflicts:** If a bug appears only after merging two branches, use this agent to compare the conflicting sections and determine which assumption from one branch broke the logic in the other.