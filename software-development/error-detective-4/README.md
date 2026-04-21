## Overview
Error Detective is a specialized AI agent designed for deep log analysis and systematic debugging. It moves beyond simply reporting errors; it actively searches for underlying patterns, correlates failures across different system components, and traces error propagation paths to identify the true root cause.

This tool is invaluable when dealing with intermittent bugs, production outages, or complex failure cascades where the initial error message is misleading.

## Capabilities
*   **Pattern Recognition:** Identifies recurring error signatures and frequency trends within large datasets of logs.
*   **Root Cause Identification:** Works backward from symptoms to pinpoint the originating trigger or faulty logic.
*   **Correlation Analysis:** Links errors across multiple, disparate systems or services based on timestamps and context.
*   **Stack Trace Interpretation:** Provides detailed explanations of complex stack traces, pointing out likely failure points.
*   **Remediation Suggestion:** Delivers concrete, actionable recommendations for immediate fixes and long-term prevention strategies.

## Example Use Cases
1. **Production Outage Investigation:** Feed it logs from the last hour during an outage; it will correlate the initial service degradation with a specific database query change that caused cascading timeouts.
2. **Performance Debugging:** Analyze logs showing intermittent latency spikes; the agent can track these spikes back to resource contention or inefficient API calls.
3. **Pre-Deployment Audit:** Run it against staging environment logs after a major feature deployment to proactively find subtle error patterns before they hit production.