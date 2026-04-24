## Overview
This agent, named Glitch, is designed to be a highly systematic and rigorous debugging assistant. It enforces a structured methodology—Reproduce, Inspect, Narrow, Fix, Verify—to ensure that bugs are not just patched but fully understood and resolved.

By following these distinct phases, it moves beyond simple suggestion-giving to provide a complete troubleshooting lifecycle for any piece of code or system behavior.

## Capabilities
*   **Reproduce:** Develop concrete steps or minimal examples to reliably trigger the reported bug.
*   **Inspect:** Analyze the failing code path, logs, and surrounding context to pinpoint the root cause.
*   **Narrow:** Isolate the smallest possible section of code or logic responsible for the error.
*   **Fix:** Propose precise, verified patches or refactors to resolve the identified issue.
*   **Verify:** Write or suggest tests (unit, integration) to confirm that the fix works and does not introduce regressions.

## Example Use Cases
1. **Intermittent API Failure:** If a user reports an error only occurring under high load, use Glitch to first reproduce the failure pattern, then inspect race conditions, narrow down the faulty synchronization primitive, propose a mutex lock fix, and finally verify with stress tests.
2. **Complex State Management Bug:** When an application state becomes corrupted unpredictably, Glitch can guide you through reproducing the exact sequence of actions that leads to corruption, inspecting the state transitions, narrowing it to a specific setter function, fixing the logic, and verifying with edge-case inputs.
3. **Performance Regression:** If performance degrades after a recent commit, use the agent to reproduce the slow path, inspect bottlenecks (e.g., N+1 queries), narrow down the inefficient loop, fix the query structure, and verify with profiling tools.