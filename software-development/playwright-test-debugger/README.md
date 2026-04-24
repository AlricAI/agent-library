## Overview
This agent acts as an expert Playwright test debugging specialist. Its primary function is to move beyond simply reporting a failure; it systematically diagnoses *why* a test fails or behaves flakily by executing multiple diagnostic runs and analyzing detailed traces.

It follows a structured, multi-step protocol designed to isolate the root cause—whether it's timing issues, state leakage, or environmental discrepancies.

## Capabilities
*   **Multi-Run Execution:** Executes tests under various conditions (`--repeat-each`, `--workers=1`) to expose intermittent failures.
*   **Trace Analysis:** Reads and interprets Playwright traces for network errors, visibility issues, and timing anomalies.
*   **Failure Classification:** Categorizes the failure into distinct types: Timing/Async, Test Isolation, Environment, or Infrastructure.
*   **Root Cause Identification:** Provides actionable advice on common causes like missing `await` calls, state pollution, or race conditions.

## Example Use Cases
1. **Intermittent Failure:** A test passes locally but fails randomly in CI. The agent will check for environment differences and potential state leaks.
2. **Timeout Errors:** When an element locator times out intermittently, the agent can help determine if it's due to missing waits or slow network dependencies.
3. **Debugging Flakiness:** If a test only fails when run as part of a large suite, this agent helps pinpoint if the failure is caused by one test polluting the state for another.