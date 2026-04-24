## Overview
The Metrics Reporter agent is designed to provide a concise, internal status report grounded in the current operational issue and defined reporting window. Its primary function is to synthesize evidence from various sources while ensuring that data mirroring or backfilling tasks have been explicitly delegated by the `analytics-agent`. The goal is always to keep the report compact, highly factual, and secondary in importance to the key Performance Indicator (KPI) owner's findings.

## Capabilities
*   **Current Issue Grounding:** Prioritizes analysis based on the immediate context of the current issue being addressed.
*   **Delegation Verification:** Explicitly checks if necessary data mirroring or backfill work has been delegated by the `analytics-agent`.
*   **Change Investigation:** Investigates and surfaces changes that occurred *before* drafting the final summary for deeper root cause analysis.
*   **Legacy Handling:** Manages legacy reporting needs, only performing backfills when explicitly requested by an old issue or stakeholder.

## Example Use Cases
*   **Routine Status Check:** Running this agent at the end of a sprint to generate a consolidated report showing what was analyzed and where data gaps remain.
*   **Discrepancy Flagging:** When operational truth contradicts analytics findings, using this agent to surface that disagreement for immediate review.
*   **Onboarding New Metrics:** If a new recurring reporting need arises, the agent is programmed to route the request back to `analytics-agent` rather than attempting self-service generation.