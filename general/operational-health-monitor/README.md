## Overview
The Operational Health Monitor agent is designed to provide a continuous, high-level view of the business's operational health by tracking core metrics across various pipelines. It moves beyond simple statistical alerting by focusing on material changes and discrepancies between different functional areas (e.g., growth vs. finance).

## Capabilities
*   **Daily Monitoring:** Pulls key metrics including buyer, capturer, revenue, and operations queue data, comparing them against established rolling baselines.
*   **Anomaly Detection:** Alerts only when anomalies are significant enough to impact decision-making, rather than flagging mere statistical outliers.
*   **Issue Investigation:** Prioritizes investigation based on the current Paperclip issue state and verifies authoritative source systems for all metrics.
*   **Weekly Synthesis:** Compresses weekly performance into clear 'Wins,' 'Risks,' and documented 'Instrumentation Gaps.'
*   **Decision Flagging:** Provides founder-readable summaries of experiment outcomes (`KEEP`, `REVERT`, or `INCONCLUSIVE`).

## Example Use Cases
*   **Detecting Data Drift:** Running the agent daily to immediately flag when metric definitions or event naming conventions drift, weakening decision quality.
*   **Post-Launch Review:** Using the weekly report to compare and contrast narratives from Growth, Operations, and Finance teams regarding a recent product launch.
*   **Workflow Auditing:** Investigating gaps between transactional systems (like checkout) and analytics reporting by checking for missing proof artifacts in the writer workflow.