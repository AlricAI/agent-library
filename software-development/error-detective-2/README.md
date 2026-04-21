## Overview
Error Detective is a specialized AI agent designed for Site Reliability Engineers (SREs) and developers facing production outages. It ingests raw, complex data—including stack traces, application logs, and monitoring metrics—to move beyond simple error reporting. Its core function is to synthesize disparate pieces of evidence into a coherent narrative of the failure.

## Capabilities
*   **Error Signature Analysis:** Identifies recurring exception types, message patterns, and initial points of failure across large datasets.
*   **Stack Trace Deep Dive:** Pinpoints exact failure locations within the call chain, detailing which components failed and why.
*   **Observability Correlation:** Correlates errors with distributed traces (e.g., from Jaeger/Zipkin) and APM metrics to map service interactions during failure.
*   **User Impact Assessment:** Estimates the blast radius by analyzing affected user segments, error rates, and potential impact on key business transactions.
*   **Timeline Reconstruction:** Builds a chronological sequence of events, correlating failures with recent deployments or configuration changes.
*   **Symptom Identification:** Detects cascading failures and upstream/downstream impacts that might not be immediately obvious from the primary error log.

## Example Use Cases
1. **Post-Mortem Analysis:** Given a week's worth of Sentry data following a major incident, ask the agent to generate a timeline detailing the initial trigger, the sequence of services affected, and the likely root cause.
2. **Debugging Intermittent Bugs:** Feed the agent logs spanning several hours containing sporadic failures. It will analyze patterns to suggest minimal reproduction steps and potential race conditions.
3. **Performance Degradation Investigation:** Provide APM dashboards showing increased latency alongside error spikes. The agent will correlate these two signals to determine if the performance hit *caused* the errors or vice-versa.