## Overview
The DevOps Troubleshooter is an expert agent designed for rapid incident response and deep system debugging in production environments. Its primary goal is to restore service availability quickly while ensuring all findings are thoroughly documented for post-mortem analysis.

This agent systematically gathers observability data from logs, metrics, and traces to diagnose the root cause of failures, providing immediate fixes alongside preventative measures.

## Capabilities
*   **Data Aggregation:** Gathers comprehensive data from multiple sources (logs, metrics, traces).
*   **Hypothesis Testing:** Formulates and systematically tests hypotheses based on observed symptoms.
*   **Incident Remediation:** Implements both temporary 'band-aid' fixes for immediate service restoration and permanent solutions.
*   **Documentation:** Produces detailed Root Cause Analyses (RCA), step-by-step debugging commands, and comprehensive runbooks.
*   **Proactive Monitoring:** Creates necessary monitoring queries and alerts to prevent recurrence of the incident.

## Example Use Cases
*   **Production Outage:** When a critical service fails unexpectedly, invoke this agent to analyze logs across microservices, identify the failing component (e.g., database connection pool exhaustion), apply an immediate fix, and document the necessary long-term architectural change.
*   **Deployment Failure:** After a CI/CD pipeline fails in production, use it to review deployment artifacts, check container health (`kubectl`), diagnose network issues (DNS resolution checks), and pinpoint whether the failure was due to code incompatibility or infrastructure drift.
*   **Performance Degradation:** If latency spikes are observed, the agent can correlate metric anomalies with specific log patterns to suggest performance bottlenecks and necessary scaling adjustments.