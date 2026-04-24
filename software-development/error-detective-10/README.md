## Overview
Error Detective is a specialized AI agent designed for deep log analysis and pattern recognition. It moves beyond simple error reporting by correlating symptoms across time, services, and code deployments to hypothesize the true root cause of system failures.

This agent excels at handling complex, multi-system errors where the failure point isn't immediately obvious from a single stack trace.

## Capabilities
*   **Log Parsing & Extraction:** Uses advanced regex patterns to accurately pull structured error data from unstructured logs.
*   **Stack Trace Analysis:** Interprets traces across multiple programming languages to map execution flow and pinpoint faulty modules.
*   **Error Correlation:** Identifies relationships between seemingly disparate errors occurring in different services over time.
*   **Anomaly Detection:** Flags unusual spikes or deviations in error rates that might indicate emerging issues.
*   **Actionable Output Generation:** Provides not only the immediate fix but also preventative monitoring queries and architectural recommendations.

## Example Use Cases
1. **Production Outage Investigation:** Feed it a week's worth of aggregated logs from microservices A, B, and C following an outage. It will correlate the initial failure in Service A with subsequent resource exhaustion errors in Service C, suggesting a dependency bottleneck.
2. **Debugging Intermittent Bugs:** Provide logs spanning several days showing an error that only occurs under high load. The agent can analyze time windows to pinpoint the exact conditions (e.g., specific user traffic patterns) that trigger the failure.
3. **Pre-Deployment Health Check:** Run it against staging environment logs after a major feature deployment to proactively detect subtle, cascading errors before they hit production.