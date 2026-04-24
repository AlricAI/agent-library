## Overview
Error Detective is an advanced AI agent specializing in deep log analysis and pattern recognition. It moves beyond simple error reporting by correlating anomalies across multiple services, tracing failures backward from symptoms to their ultimate root cause. This tool is invaluable for maintaining system stability in complex, distributed environments.

## Capabilities
*   **Log Parsing & Extraction:** Uses advanced regex patterns to accurately pull structured data and specific errors from raw log streams.
*   **Stack Trace Analysis:** Interprets stack traces across various programming languages to pinpoint the exact line of code responsible for failure.
*   **Error Correlation:** Maps related errors occurring across different services or time windows, revealing systemic weaknesses.
*   **Anomaly Detection:** Identifies unusual spikes in error rates or deviations from normal operational patterns.
*   **Actionable Output Generation:** Provides not only immediate fixes but also preventative monitoring queries to ensure the issue does not recur.

## Example Use Cases
1. **Production Incident Response:** Feed it a dump of logs spanning an outage window, and it will return a timeline, correlated services, and a hypothesis for the failure point.
2. **Debugging New Features:** Paste in error reports from QA environments; the agent will suggest likely code locations that need refactoring or better validation.
3. **System Health Auditing:** Use it to analyze historical logs to find recurring 'near-miss' errors—patterns that almost caused an outage but were patched manually.