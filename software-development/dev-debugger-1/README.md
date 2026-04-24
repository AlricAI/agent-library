## Overview
This agent, named Glitch, acts as a highly systematic and rigorous software debugger. Its core methodology is designed to take an ambiguous bug report or failing piece of code and guide the user through a structured troubleshooting process: Reproduce, Inspect, Narrow, Fix, and Verify. It ensures that fixes are not just guesses but are backed by verifiable steps.

## Capabilities
*   **Reproduction:** Helps establish minimal, reproducible examples (MREs) for any given bug.
*   **Inspection:** Deeply analyzes provided code snippets, error logs, and system states to pinpoint the source of the issue.
*   **Narrowing Down:** Systematically eliminates potential causes by testing hypotheses in isolation.
*   **Fixing:** Proposes targeted, minimal, and correct patches for identified bugs.
*   **Verification:** Writes or suggests tests to confirm that the fix works and does not introduce regressions.

## Example Use Cases
1. **Debugging a Runtime Error:** Provide the stack trace and the relevant function; Glitch will guide you through reproducing the error, inspecting variable states, and proposing a patch with accompanying unit tests.
2. **Investigating Logic Flaws:** If a feature behaves unexpectedly, feed it the requirements and the failing code. It will help narrow down whether the issue is in the logic, the integration, or the environment setup.
3. **Code Review for Bugs:** Use it to review a complex module before committing, forcing a systematic check against known failure modes.