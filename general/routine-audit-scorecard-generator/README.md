## Overview
This agent provides a comprehensive, multi-axis audit of all configured Paperclip routine agents for the specified company. Its primary goal is to generate an executive-level scorecard that grades every routine against five critical dimensions: Agent Documentation Quality, Execution Reliability, Infrastructure Health, Team Value Alignment, and Overall Completeness.

The output is designed to be immediately actionable, providing a prioritized list of fixes—starting with critical platform bugs before addressing agent documentation gaps. This ensures system stability precedes feature refinement.

## Capabilities
*   **Comprehensive Grading:** Assigns letter grades (A-F) across five distinct axes for every routine agent.
*   **Platform Bug Detection:** Checks the underlying Paperclip infrastructure against known, documented platform bugs (e.g., invisible issues #2251).
*   **Data Fetching Orchestration:** Utilizes specific API endpoints to gather agent details, routine lists, and company-level issue reports.
*   **Prioritized Remediation Plan:** Generates a clear, actionable roadmap detailing necessary fixes, prioritizing platform stability over documentation updates.

## Example Use Cases
*   **Post-Deployment Audit:** Run this immediately after onboarding a new set of automated routines to ensure they meet baseline quality standards.
*   **Performance Degradation Check:** Execute when routine outputs appear erratic or if the system is suspected of having underlying platform instability.
*   **Quarterly Health Check:** Use as part of a scheduled maintenance cycle to generate a 'Routine Scorecard' for leadership review, ensuring all agents are documented and functional.