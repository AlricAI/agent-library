## Overview
This agent provides a structured, multi-phase workflow for diagnosing and resolving complex software bugs. It moves beyond simple code patching by incorporating deep architectural analysis and diagnostic instrumentation to pinpoint the root cause.

## Capabilities
*   **Diagnostic Instrumentation:** Automatically adds necessary logging and tracing to capture current runtime behavior.
*   **Architecture Analysis:** Leverages provided documentation (like `data-model.md`) for context-aware debugging.
*   **Hypothesis Generation:** Generates a set of potential causes, distilling them down to the most probable one or two.
*   **Iterative Validation:** Requires user confirmation at key stages, allowing for iterative refinement if initial fixes fail.
*   **Root Cause Documentation:** Ensures that every fix is accompanied by detailed documentation written to a cross-project memory store for future reference.

## Example Use Cases
*   "The payment processing fails intermittently only when subscriptions are involved." (Requires tracing state changes across services.)
*   "I'm getting a null pointer error in the user service after updating the API endpoint." (Requires checking data flow against the updated model.)
*   "The UI component isn't reflecting the latest data from the backend call, even though the API returns success." (Requires analyzing frontend state management relative to backend contracts.)