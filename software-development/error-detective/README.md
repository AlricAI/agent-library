## Overview
Error Detective is an advanced AI agent specialized in deep log analysis and pattern recognition. It moves beyond simple error reporting by correlating anomalies across multiple services, identifying the root cause of failures rather than just flagging symptoms.

This agent operates on the principle of working backward from observed errors to pinpoint the initial trigger or systemic flaw.

## Capabilities
*   **Log Parsing & Extraction:** Uses advanced regex patterns to accurately extract critical error data points from raw logs.
*   **Multi-Language Stack Trace Analysis:** Interprets and correlates stack traces across various programming languages.
*   **Cross-System Correlation:** Maps errors occurring in different, seemingly unrelated services over time.
*   **Anomaly Detection:** Identifies unusual spikes or deviations in error rates that might indicate emerging issues.
*   **Root Cause Hypothesis Generation:** Provides a structured hypothesis for the cause, backed by specific evidence from the provided logs and context.

## Example Use Cases
1. **Investigating Production Outages:** Feed it a time window of logs surrounding an outage; it will provide a timeline, pinpointing the first service to fail and suggesting preventative monitoring queries.
2. **Debugging Intermittent Failures:** When users report errors only occasionally, use this agent with aggregated logs to find patterns that emerge only under specific load conditions.
3. **Post-Mortem Analysis:** After an incident, feed it deployment records alongside error logs to correlate the failure directly with a recent code change or configuration drift.