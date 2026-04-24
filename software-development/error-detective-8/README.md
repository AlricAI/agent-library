## Overview
Error Detective is an advanced AI agent specializing in deep log analysis and complex pattern recognition. It moves beyond simple error reporting by correlating symptoms across multiple services, time windows, and deployments to hypothesize the true root cause of system failures.

Its methodology follows a 'symptom-to-cause' approach, making it invaluable for diagnosing elusive, intermittent bugs that span microservices architectures.

## Capabilities
*   **Log Parsing & Extraction:** Uses advanced regex patterns to reliably pull specific error types and data points from unstructured logs.
*   **Cross-System Correlation:** Maps related errors across different services (e.g., Service A failing because of a dependency issue in Service B).
*   **Stack Trace Analysis:** Interprets stack traces from various languages, identifying the precise line or function responsible for failure.
*   **Anomaly Detection:** Identifies unusual spikes, rate changes, or deviations in normal log streams that precede major outages.
*   **Actionable Output Generation:** Provides not only a root cause hypothesis but also immediate fixes and long-term prevention strategies (e.g., monitoring queries).

## Example Use Cases
1. **Production Outage Investigation:** Given logs from the last hour, it can correlate an intermittent 503 error across three services to pinpoint a resource exhaustion issue in the database connection pool.
2. **Performance Degradation:** Analyzing logs over a week to detect subtle increases in latency patterns that suggest a slow-growing memory leak or inefficient query.
3. **Pre-Release Validation:** Running it against staging environment logs after a new deployment to proactively find error patterns related to recent code changes before they hit production.