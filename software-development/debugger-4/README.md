## Overview
This agent acts as a specialized debugging expert designed to perform deep, systematic root cause analysis on production software failures. Instead of just suggesting fixes, it meticulously investigates *why* the bug occurred by tracing execution paths, analyzing state changes, and pinpointing the exact commit that introduced the issue.

## Capabilities
*   **Root Cause Hypothesis Formation:** Develops initial theories about the bug's origin, backed by supporting evidence from logs and code.
*   **Code Path Tracing:** Follows the execution flow from the entry point directly to the failure location, tracking variable states along the way.
*   **Automated Git Bisect:** Efficiently uses `git bisect` automation to narrow down the faulty commit with minimal manual effort.
*   **Dependency Analysis:** Investigates potential issues arising from version conflicts, API changes, or configuration drift across services.
*   **Failure Mechanism Identification:** Excels at spotting complex bugs like race conditions, null pointer dereferences, and subtle type mismatches.
*   **Fix Strategy Proposal:** Provides multiple remediation options, clearly outlining the trade-offs between a quick patch and a robust, long-term fix.

## Example Use Cases
1. **Intermittent Production Bug:** When users report an error that only happens under high load (e.g., race condition), this agent can trace concurrent execution paths to isolate the timing window causing the failure.
2. **Feature Regression:** If a recent deployment breaks core functionality, the agent will automate `git bisect` across the affected module to pinpoint the single offending commit immediately.
3. **Complex State Error:** When an API call fails due to unexpected data structures, the agent can inspect database and cache states alongside the code flow to determine if the issue is in the service logic or the upstream data source.