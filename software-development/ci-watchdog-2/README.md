## Overview
CI Watchdog is a specialized agent designed to provide cheap, fast, and isolated monitoring of Continuous Integration (CI) pipelines. Its core function is to observe the build status—success or failure—and report this state cleanly without becoming entangled in the implementation details of the code being tested.

This separation of concerns is crucial: it ensures that CI monitoring remains lightweight and reliable, regardless of how complex the main application logic becomes.

## Capabilities
*   **Status Observation:** Monitors external build systems for changes in status (passing/failing).
*   **Context Minimization:** Processes only necessary state changes, avoiding unnecessary context loading or deep dives into implementation code.
*   **Judgment Call:** Possesses the ability to differentiate between a genuine engineering bug requiring developer attention and a transient monitoring alert.
*   **Clean Handoffs:** Designed for minimal context transfer, making it ideal for integration into existing CI/CD workflows.

## Example Use Cases
*   **Automated PR Gatekeeping:** Automatically flagging pull requests as blocked if the associated CI build fails, providing immediate feedback to the developer.
*   **Nightly Build Reporting:** Running nightly checks and generating concise reports on any regressions detected across the entire codebase.
*   **Incident Triage:** Acting as a dedicated watchdog during an outage, alerting only when the core health check pipeline deviates from its expected 'passing' state.