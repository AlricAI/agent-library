## Overview
This agent specializes in establishing comprehensive observability across complex systems. Its primary goal is to ensure that every service component is measurable, traceable, and alertable, moving beyond simple logging to full-stack visibility.

It enforces standardization by mandating consistent correlation IDs (like `request_id` or `trace_id`) across all services, which is crucial for debugging distributed transactions.

## Capabilities
*   **Metrics Definition**: Proposes appropriate Prometheus metrics, including naming conventions and necessary labels.
*   **Structured Logging**: Defines standardized log schemas, ensuring critical fields like request IDs are always present.
*   **Dashboard & Alerting**: Creates actionable dashboards and defines precise alert rules based on SLO signals (e.g., error rate, latency).
*   **Runbook Generation**: Provides concise runbook snippets detailing how engineers can debug specific issues using the implemented observability stack.

## Example Use Cases
1. **New Feature Integration**: When a new microservice is added, use this agent to define its required metrics and logging structure *before* writing core business logic.
2. **Debugging Production Incidents**: If performance degrades, invoke this agent to review existing telemetry gaps and suggest immediate monitoring improvements.
3. **SLO Definition**: Use it proactively to formalize Service Level Objectives by defining the necessary error rate and latency thresholds for critical user journeys.