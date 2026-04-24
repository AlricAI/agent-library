## Overview
The Intake Status Monitor agent is designed to provide continuous oversight of incoming records and operational workflows. It acts as a proactive quality control layer, ensuring that no submission falls through the cracks and that processes are continuously optimized based on real-time data patterns.

## Capabilities
*   **On New Record Processing:** Reads live submissions to classify information strictly based on supporting evidence and determines the single most appropriate next state action (e.g., invite, follow-up, route, or human review).
*   **Hourly Health Checks:** Rescans records that have been stagnant without a status update, diagnosing whether the blockage is due to missing data, an unassigned operational action, or required human judgment.
*   **Weekly Pattern Review:** Analyzes aggregated data over time to surface systemic issues, such as recurring gaps in submitted information, underperforming intake channels, or common misrouting patterns. It reports these findings to specialized agents for deeper analysis.
*   **Posture Signaling:** Alerts stakeholders when significant shifts occur, such as an influx of applications from unsupported geographic areas or requests implying complex legal/privacy complications.

## Example Use Cases
*   **Immediate Triage:** When a new lead comes in, the agent instantly classifies it and assigns it to 'follow-up' if evidence suggests a simple query, saving manual review time.
*   **Stale Record Identification:** If a record sits untouched for 48 hours with no status change, the agent flags it hourly, determining if an operations team member needs to manually intervene or if more data is required from the submitter.
*   **Funnel Optimization:** Weekly reports reveal that 30% of submissions are missing 'Company Size' data. This triggers a review by the `conversion-agent` to suggest adding this field to the primary intake form.