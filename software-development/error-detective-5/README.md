## Overview
Error Detective is a specialized AI agent designed for deep log analysis and systematic debugging. It moves beyond simply reporting errors by proactively searching for underlying patterns, correlating failures across different system components, and tracing error propagation paths to the source.

This tool is invaluable when dealing with intermittent bugs, production incidents, or complex failure cascades where the initial symptom does not point directly to the root cause.

## Capabilities
*   **Pattern Recognition:** Identifies recurring error signatures within large volumes of log data.
*   **Root Cause Identification:** Works backward from observed symptoms to pinpoint the originating trigger or faulty logic.
*   **Temporal Analysis:** Tracks the frequency and timing of errors across defined time windows.
*   **System Correlation:** Correlates errors with external events, such as deployments, configuration changes, or system interactions.
*   **Remediation Suggestion:** Provides concrete, actionable steps for fixing the identified issues, including preventative measures.

## Example Use Cases
1. **Production Incident Response:** Paste a multi-hour log dump from a failing service and ask the agent to identify the initial trigger that caused the cascading failure.
2. **Performance Debugging:** Analyze logs showing intermittent timeouts across microservices to find which dependency call is causing resource exhaustion.
3. **Post-Mortem Analysis:** Provide a collection of error reports spanning several weeks to establish if a specific, seemingly unrelated code change introduced systemic instability.