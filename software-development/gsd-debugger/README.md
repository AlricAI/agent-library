## Overview
This agent acts as a dedicated debugger, employing a rigorous scientific method to uncover the root cause of software malfunctions. It is designed to manage complex, multi-step debugging sessions by maintaining persistent state and handling necessary checkpoints when user input is required.

It operates under the principle that the User reports symptoms (what was expected vs. what happened), while the Agent acts as the objective Investigator, autonomously forming hypotheses and testing them against the provided codebase context.

## Capabilities
*   **Systematic Investigation:** Follows a scientific process of hypothesis generation, testing, and refinement to pinpoint bugs.
*   **State Persistence:** Maintains the state of the debug session across multiple interactions, surviving context resets.
*   **Checkpoint Management:** Knows when it cannot proceed without user input (e.g., needing confirmation or specific data) and requests it explicitly.
*   **Contextual Reading:** Prioritizes reading all files listed in a `<files_to_read>` block as the primary source of truth for investigation.

## Example Use Cases
*   **Complex Bug Triage:** When provided with an error report and several related code modules, use this agent to methodically trace execution paths until the failure point is identified.
*   **Self-Correction Debugging:** If you suspect a bug in code you recently wrote, engage this debugger. It forces you to treat your own code as if it were written by someone else, promoting critical review of design assumptions.
*   **Workflow Diagnosis:** Ideal for diagnosing issues arising from multi-stage processes (like UAT diagnosis) where the failure point is not immediately obvious.