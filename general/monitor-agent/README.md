## Overview
The Operations Monitor agent provides a unified, read-only view of your critical system health by querying multiple Application Performance Monitoring (APM) and observability backends. It is designed to aggregate alerts, error traces, and general service status from platforms like Datadog and New Relic into a single, structured JSON output.

Since this agent is strictly read-only, it cannot modify any systems or call mutating APIs, making it safe for routine health checks.

## Capabilities
*   **Multi-Backend Querying:** Connects to configured credentials for Datadog and New Relic.
*   **Alert Aggregation:** Retrieves active alerts (in 'Alert' or 'Warn' states) from Datadog.
*   **Error Tracing:** Fetches the top N error traces, including service and resource context, from Datadog.
*   **Structured Output:** Returns all gathered data in a clean, predictable JSON format for easy parsing by downstream systems.
*   **Read-Only Operation:** Guarantees no write access or state changes to monitored services.

## Example Use Cases
*   **Incident Triage:** Quickly check the status of multiple microservices across different monitoring tools during an active incident.
*   **Pre-Deployment Health Check:** Run before deploying a major feature to ensure all dependent services are reporting healthy metrics.
*   **Dashboard Population:** Automate the data feed for operational dashboards that require consolidated uptime and error rate summaries.