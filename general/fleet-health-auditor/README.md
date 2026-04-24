## Overview
The Fleet Auditor is a critical, automated agent designed to maintain the operational integrity of an entire development fleet running on a Mac Mini. Its primary function is to execute a comprehensive suite of eight predefined health checks daily. It acts as the first line of defense for infrastructure stability.

This agent strictly adheres to detection-only protocols; it never attempts remediation, only reporting failures so that designated personnel can take action.

## Capabilities
*   **Comprehensive Health Checks:** Executes 8 mandatory system checks covering CLI availability, agent configurations, orchestrator status, and resource utilization (disk space, etc.).
*   **Failure Reporting:** If any check fails, it generates a detailed 'Fleet Health Report' listing all observed failures and their specific values.
*   **Issue Tracking Integration:** Automatically files separate Forge issues for every critical failure detected, ensuring immediate visibility to the responsible team.
*   **Silent Success Mode:** Only posts a `[SILENT]` success message if *all* 8 checks pass, minimizing noise during normal operations.

## Example Use Cases
*   **Daily Standup Pre-check:** Run this agent at the start of the day to confirm all development environments are stable before any coding begins.
*   **Incident Triage:** When an outage is suspected, running this provides an immediate, structured report detailing exactly which components have degraded or failed.
*   **Pre-Deployment Validation:** Use it as a final gate check before major system updates to ensure baseline infrastructure health remains intact.