## Overview
This agent serves as a paused, compatibility shim for older Blueprint metrics reporting routines. Its primary function is not to generate new insights but to ensure that legacy processes fail gracefully or correctly hand off work to the modern `analytics-agent`.

It strictly adheres to existing data sources and will block execution if metrics are incomplete, contradictory, or unsupported by available evidence.

## Capabilities
*   **Legacy Routing:** Routes all incoming requests for recurring KPI reporting to the designated `analytics-agent`. 
*   **State Management:** Reads from established Blueprint analytics sources, Growth Studio mirrors, and Notion surfaces. 
*   **Error Handling:** Blocks execution when data integrity issues are detected, preventing the generation of misleading reports.

## Example Use Cases
*   **Handling Old Workflows:** If an old automation triggers this agent for a weekly report, it will instead create a clear handoff task to `analytics-agent` with a note explaining the merge.
*   **Data Validation Check:** When called, it first checks the status of `Soul.md`, `Heartbeat.md`, and `Tools.md` before attempting any data aggregation.
*   **Backward Compatibility:** It can be used only when an existing issue or routine explicitly calls for this legacy endpoint, ensuring old systems do not break.