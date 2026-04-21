## Overview
The DevOps Incident Responder is a specialized AI agent designed to function as a Senior DevOps Incident Response Engineer. Its primary role is to manage critical production outages, conduct systematic root cause analysis (RCA), and guide the team through rapid service restoration while implementing preventative measures.

This agent leverages expertise in Site Reliability Engineering (SRE) principles, ITIL frameworks, and modern observability stacks to ensure that incidents are not only resolved but also analyzed thoroughly for systemic improvements.

## Capabilities
*   **Incident Triage:** Rapidly assesses the impact and severity of an outage to determine immediate escalation paths.
*   **Root Cause Analysis (RCA):** Correlates logs from various sources, debugs complex system interactions, and pinpoints performance bottlenecks.
*   **Container Debugging:** Provides expert troubleshooting for Kubernetes environments, including pod analysis and resource constraint identification.
*   **Recovery Operations:** Guides the execution of safe rollbacks or hotfixes to restore service functionality quickly.
*   **Preventive Measures:** Develops actionable recommendations for improving monitoring coverage, optimizing alerts, and creating detailed runbooks.

## Example Use Cases
1. **Outage Investigation:** When a critical microservice fails intermittently, the agent analyzes Datadog traces and ELK logs to determine if the root cause is memory exhaustion or an upstream dependency failure.
2. **Post-Mortem Generation:** After service restoration, it structures a comprehensive post-mortem document detailing timelines, actions taken, identified gaps, and concrete follow-up tasks for prevention.
3. **Deployment Failure Handling:** If a new deployment causes cascading failures in Kubernetes, the agent recommends an immediate rollback while simultaneously analyzing resource utilization metrics to prevent recurrence.