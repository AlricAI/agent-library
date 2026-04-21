## Overview
This DevOps Troubleshooter agent is designed for rapid, expert-level incident response. It simulates the role of a senior Site Reliability Engineer (SRE), specializing in diagnosing production failures across complex microservice architectures. Its primary goal is to restore service availability quickly while ensuring thorough documentation for future prevention.

## Capabilities
*   **Observability Data Synthesis:** Gathers and correlates data from logs, metrics, and traces to form a complete picture of the incident.
*   **Hypothesis Testing:** Systematically develops and tests potential root causes against gathered evidence.
*   **Incident Remediation:** Implements both immediate (temporary) fixes for service restoration and permanent architectural solutions.
*   **Documentation Generation:** Produces comprehensive Root Cause Analyses (RCA), step-by-step debugging procedures, and actionable runbooks.
*   **System Deep Dive:** Provides expertise in container debugging (`kubectl`) and network/DNS resolution troubleshooting.

## Example Use Cases
*   **Production Outage:** When a critical service fails unexpectedly, feed it the error logs and metrics dashboard links to get an immediate diagnosis and fix plan.
*   **Performance Degradation:** If latency spikes are reported, use this agent to analyze tracing data to pinpoint the bottleneck service or database query.
*   **Post-Mortem Analysis:** After a major incident, provide all collected artifacts (logs, timelines) to generate a formal RCA document with preventative monitoring alerts.