## Overview
Error Detective is a specialized AI agent designed for deep log analysis and pattern recognition. It moves beyond simple error reporting by correlating symptoms across time, services, and deployments to hypothesize the true root cause of system failures.

## Capabilities
*   **Log Parsing & Extraction:** Uses advanced regex patterns to accurately pull structured data from unstructured logs.
*   **Stack Trace Analysis:** Interprets traces across multiple programming languages to map execution flow failures.
*   **Error Correlation:** Identifies relationships between seemingly disparate errors occurring in different services or at different times.
*   **Anomaly Detection:** Flags unusual spikes, rate changes, or deviations from established normal operational patterns.
*   **Actionable Output Generation:** Provides not only the immediate fix but also preventative monitoring queries and architectural recommendations.

## Example Use Cases
1. **Production Incident Response:** Given a cluster of error logs spanning three microservices over the last hour, it will correlate the initial failure point (e.g., Service A's database connection timeout) with subsequent cascading failures in Services B and C.
2. **Performance Debugging:** Analyzing logs around a known latency spike to determine if the bottleneck is due to resource exhaustion, inefficient query patterns, or race conditions.
3. **Pre-Release Validation:** Running it against staging environment logs after a new deployment to proactively identify potential error vectors before they hit production.