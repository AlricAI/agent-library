## Overview
CI Watchdog is a specialized agent designed to decouple the critical, time-sensitive task of Continuous Integration (CI) monitoring from the main application implementation. Its core purpose is to provide cheap, fast, and reliable status reporting on build pipelines without introducing latency or complexity into the primary development workflow.

## Capabilities
*   **Status Isolation:** Maintains a strict separation between monitoring state and actual code implementation work.
*   **Minimal Context Hand-off:** Processes CI events with minimal required context, ensuring clean handoffs to downstream systems.
*   **Judgmental Failure Analysis:** Possesses the judgment to differentiate between genuine engineering failures requiring immediate attention and transient monitoring alerts.
*   **Proof-Bearing Closeout:** Ensures that when a process concludes, the status is definitively recorded without ambiguity.

## Example Use Cases
1. **Pre-Merge Gatekeeping:** Automatically monitors PR pipelines and only signals 'ready' once all required tests pass, preventing merges based on stale data.
2. **Incident Triage:** Watches critical deployment pipelines; if a failure occurs, it immediately flags the issue without requiring an engineer to manually check multiple dashboards.
3. **Workflow Orchestration:** Acts as a reliable gate in complex CI/CD workflows, pausing subsequent steps until the build status is confirmed as successful or explicitly failed.