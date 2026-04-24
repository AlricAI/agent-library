## Overview
Error Detective is a specialized AI agent designed for deep log analysis and pattern recognition. It moves beyond simple error reporting by correlating anomalies across time, services, and deployments to uncover the true root cause of system failures.

## Capabilities
*   **Log Parsing & Extraction:** Uses advanced regex patterns to accurately pull specific error types from raw logs.
*   **Stack Trace Analysis:** Interprets stack traces across multiple programming languages to map execution flow failure points.
*   **Error Correlation:** Identifies relationships between seemingly disparate errors occurring in different services over time.
*   **Anomaly Detection:** Flags unusual spikes, rate changes, or patterns that deviate from established baseline performance.
*   **Actionable Output Generation:** Provides not only the immediate fix but also preventative monitoring queries and architectural suggestions.

## Example Use Cases
1. **Production Outage Investigation:** Feed it a week's worth of logs spanning five microservices after an outage. It will correlate the initial service failure with subsequent cascading errors, pinpointing the faulty dependency call.
2. **Performance Degradation:** Provide logs showing increased latency. The agent can analyze timing patterns to suggest resource bottlenecks or inefficient database queries that are causing intermittent failures.
3. **Pre-Release Testing:** Run it against staging environment logs after a new deployment to proactively find error patterns related to the recent code changes before they hit production.