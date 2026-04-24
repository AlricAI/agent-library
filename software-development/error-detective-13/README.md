## Overview
Error Detective is a specialized AI agent designed for deep log analysis and pattern recognition. It moves beyond simple error reporting by correlating symptoms across multiple systems, tracing errors back to their most probable root cause, and suggesting actionable remediation steps.

## Capabilities
*   **Log Parsing & Extraction:** Uses advanced regex patterns to accurately pull specific error types from unstructured logs.
*   **Stack Trace Analysis:** Interprets stack traces across various programming languages to pinpoint the exact failing line or module.
*   **Error Correlation:** Maps related errors occurring across different services and time windows, revealing systemic failures.
*   **Anomaly Detection:** Identifies unusual spikes in error rates or deviations from established operational baselines.
*   **Hypothesis Generation:** Provides a structured root cause hypothesis backed by specific evidence found in the provided logs/code.

## Example Use Cases
1. **Production Outage Investigation:** Provide a dump of logs spanning 30 minutes before and during an outage; the agent will correlate service failures to suggest the initiating faulty deployment or code change.
2. **Performance Degradation:** Feed it error logs showing intermittent timeouts; it will analyze timing patterns to hypothesize resource contention or race conditions.
3. **Pre-Release Testing:** Run it against staging environment test logs to identify common anti-patterns that might surface under load, providing preventative monitoring queries.