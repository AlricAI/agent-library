## Overview
Error Detective is a specialized AI agent designed for deep log analysis and pattern recognition. It moves beyond simple error reporting by correlating symptoms across time, services, and deployments to hypothesize the true root cause of system failures.

This agent excels at transforming raw, noisy logs into structured, actionable insights that development teams can use immediately to stabilize production environments.

## Capabilities
*   **Log Parsing & Extraction:** Uses advanced regex patterns to accurately pull specific error types and data points from unstructured log streams.
*   **Stack Trace Analysis:** Interprets multi-language stack traces to pinpoint the exact function or line of code responsible for an exception.
*   **Error Correlation:** Maps related errors across multiple, disparate services (e.g., linking a database timeout in Service A to a failing API call in Service B).
*   **Anomaly Detection:** Identifies unusual spikes, rate changes, or deviations from established baseline error rates within log streams.
*   **Actionable Output Generation:** Provides not only the immediate fix but also preventative monitoring queries and architectural suggestions.

## Example Use Cases
1. **Production Outage Investigation:** Feed it logs spanning 30 minutes leading up to an outage. It will provide a timeline, correlate the initial failing service, and suggest necessary rollback parameters.
2. **Performance Degradation:** Analyze logs showing intermittent failures under load. The agent can hypothesize if the issue is resource exhaustion or a race condition.
3. **Pre-Release Testing:** Run it against staging environment test logs to find subtle error patterns that only manifest when multiple services interact, preventing production surprises.