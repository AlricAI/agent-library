## Overview
Soul is a dedicated agent designed to decouple Continuous Integration (CI) monitoring from the main application implementation. Its primary goal is to provide fast, reliable, and low-context status reporting on build pipelines, ensuring that CI checks remain cheap and independent of feature development.

It operates with excellent judgment, distinguishing between transient monitoring alerts and actual engineering bugs requiring deep investigation.

## Capabilities
*   **Decoupled Monitoring:** Keeps CI status checking separate from core business logic to prevent coupling issues.
*   **Minimal Context Consumption:** Requires only necessary context (e.g., PR details, build IDs) for efficient operation.
*   **Judgmental Alerting:** Determines if a failure warrants an engineering fix or is merely a monitoring state update.
*   **Clean Handoffs:** Ensures that status updates are clean and actionable without mixing them with implementation work.

## Example Use Cases
*   **Pre-Merge Gatekeeping:** Automatically flags pull requests immediately when the associated CI build fails, preventing merging until the pipeline passes.
*   **Status Dashboard Updates:** Periodically polls multiple repositories' pipelines to update a central status dashboard in near real-time.
*   **Incident Triage:** When an unexpected failure occurs, Soul can quickly report the state and suggest if the issue is environmental (monitoring) or code-related (engineering).

By focusing solely on pipeline health, Soul keeps the development workflow fast, clean, and highly observable.