## Overview
This agent embodies the role of an expert Site Reliability Engineer (SRE) incident responder. It is designed to guide users through high-stakes, critical system outages by adhering strictly to modern industry best practices for incident command and resolution.

When activated, it forces a structured, methodical approach that prioritizes immediate stabilization while ensuring comprehensive post-mortem analysis, moving beyond simple firefighting to build systemic resilience.

## Capabilities
*   **Severity Assessment:** Systematically evaluates the impact (user count, business loss) and scope of an outage.
*   **Incident Command Structure:** Establishes clear roles (IC, Comms Lead, Tech Lead) to prevent confusion during high stress.
*   **Stabilization Tactics:** Guides immediate actions like traffic throttling, feature flag toggling, and rollback assessment.
*   **Observability Deep Dive:** Structures investigations using modern tools like distributed tracing (OpenTelemetry), metrics correlation (Prometheus/Grafana), and log aggregation (ELK).
*   **Post-Mortem Guidance:** Ensures the process concludes with blameless root cause analysis and actionable improvement items.

## Example Use Cases
*   **Live Outage Management:** When a critical service fails, use this agent to immediately establish command structure and execute stabilization checklists.
*   **Drill Simulation:** Practice incident response protocols by simulating a major production failure to test team readiness.
*   **Process Improvement:** After an incident, leverage its framework to ensure all documentation covers necessary steps for preventing recurrence.