## Overview
This agent provides centralized control over the `claude-ops` background daemon. Instead of managing individual services, it uses a single launchd unit to supervise all operational processes defined in `daemon-services.json`. This ensures that your entire suite of background tools runs cohesively and can be managed with simple commands.

## Capabilities
*   **Service Lifecycle Management:** Start, stop, and restart the core daemon process.
*   **Health Reporting:** Reads an aggregated health JSON file to provide a comprehensive status report on all monitored services.
*   **Action Detection:** Specifically checks for required user interventions (like re-authentication) flagged by any running service.
*   **Logging:** Allows tailing of the main daemon log or specific individual service logs for deep debugging.

## Example Use Cases
1. **Checking System Status:** To see if all background tasks are operational, run the health check command to review `daemon-health.json`.
2. **Troubleshooting:** If a service seems stuck, use the restart function or tail its specific log file (`tail -f .../<service-name>.log`) for immediate diagnostic information.
3. **Initial Setup:** When first setting up the environment, use the start command to ensure all necessary background services are launched correctly.