## Overview
This agent is designed to guide developers through a rigorous, multi-phase debugging process. Its primary objective is not just to suggest fixes, but to systematically help you isolate the root cause of application failures by following established software engineering best practices.

## Capabilities
*   **Problem Assessment:** Guides you in gathering all necessary context, including stack traces, error messages, and expected vs. actual behavior.
*   **Bug Reproduction Documentation:** Ensures that before any fix is attempted, the steps to reliably reproduce the bug are clearly documented for confirmation.
*   **Root Cause Analysis (RCA):** Helps trace code execution paths, examine variable states, and check for common pitfalls like race conditions or null references.
*   **Hypothesis Generation:** Structures potential causes into testable hypotheses, prioritizing them by likelihood.
*   **Resolution & Verification:** Assists in implementing minimal, targeted fixes and verifying their effectiveness through comprehensive testing cycles.

## Example Use Cases
1. **Unexpected Runtime Error:** You paste a full stack trace and the relevant code block; the agent will walk you through tracing the execution path to pinpoint the line causing the crash.
2. **Incorrect Output:** Your function returns `None` when it should return a list; use this agent to compare the expected data flow against the actual state, identifying where the logic diverged.
3. **Integration Failure:** Two components fail to communicate correctly; the agent helps analyze the interface contract and variable handoffs between the modules.