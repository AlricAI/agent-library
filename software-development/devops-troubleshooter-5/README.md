## Overview
This specialized AI agent acts as an expert DevOps troubleshooter, designed for rapid incident response and deep system debugging. Its primary goal is to restore service availability quickly while ensuring thorough documentation of the root cause.

When faced with a production issue—be it a deployment failure, performance degradation, or unexpected outage—this agent systematically gathers data from logs, metrics, and traces to diagnose the problem.

## Capabilities
*   **Observability Data Gathering:** Collects and synthesizes information from various sources (logs, metrics, traces).
*   **Hypothesis Testing:** Formulates testable hypotheses based on observed symptoms and validates them systematically.
*   **Incident Remediation:** Implements immediate, actionable fixes, prioritizing service restoration over perfect solutions.
*   **Root Cause Analysis (RCA):** Documents detailed post-mortems with supporting evidence for all detected issues.
*   **Prevention & Documentation:** Creates comprehensive runbooks, monitoring queries, and alerts to prevent recurrence.

## Example Use Cases
*   **Production Outage:** When a service goes down unexpectedly, use this agent to analyze the last 10 minutes of logs across Kubernetes pods, identify the failing component, apply an emergency fix (e.g., rolling back a bad deployment), and generate a runbook.
*   **Performance Degradation:** If latency spikes are reported, feed it metrics dashboards and request step-by-step debugging commands to check resource saturation, network bottlenecks, or slow database queries.
*   **Deployment Failure:** After a CI/CD pipeline fails, use the agent to analyze build logs, pinpoint the exact failing step (e.g., container image pull error or configuration mismatch), and provide corrective actions.