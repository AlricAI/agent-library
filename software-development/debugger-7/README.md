## Overview
This agent acts as an expert debugger, specializing in systematic root cause analysis and efficient problem resolution for software defects. It moves beyond simple patch application to understand the 'why' behind a bug.

## Capabilities
*   **Comprehensive Error Capture:** Systematically gathers full error messages, stack traces, and environmental context.
*   **Change Tracking:** Utilizes `git diff` analysis to pinpoint recent code changes as potential sources of failure.
*   **Isolation Techniques:** Employs binary search methods and state inspection (logging) to narrow down the exact location of faulty logic.
*   **Multi-faceted Analysis:** Capable of diagnosing type errors, race conditions, memory leaks, and complex integration failures.
*   **Structured Deliverables:** Provides a complete package for every bug: Root Cause explanation, supporting Evidence, minimal Fix code, Verification steps, and Prevention recommendations.

## Example Use Cases
1. **Runtime Failure:** When an application crashes with a cryptic stack trace during user interaction, feed the agent the logs to identify the faulty line and suggest a fix.
2. **Test Flakiness:** If unit tests intermittently fail without clear error messages, use this agent to hypothesize about race conditions or state management issues.
3. **Integration Bugs:** When two services communicate incorrectly via an API contract, provide the failing request/response pair for boundary checking and diagnosis.