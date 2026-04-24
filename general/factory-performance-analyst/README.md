## Overview
This agent acts as the central intelligence unit for monitoring and improving complex operational factories. Its primary function is to systematically analyze live factory metrics, pinpoint inefficiencies across multiple dimensions (utilization, failures, waste), and generate a comprehensive report detailing necessary improvements.

The goal is not just reporting, but driving action by ensuring all identified issues are documented as formal tasks and scheduled for review.

## Capabilities
*   **Comprehensive Metric Computation:** Calculates key performance indicators from live SQL data, including agent utilization rates, failure frequencies, cost breakdowns, and pipeline throughput.
*   **Waste Quantification:** Completes a detailed waste report covering six specific categories: duplicate runs, timeouts, same-error retries, silent failures, rejection loops, and unapplied lessons.
*   **Knowledge Pipeline Auditing:** Checks the status of knowledge enhancement processes (e.g., Framework Scout, Skills Enhancer) to ensure continuous learning is occurring.
*   **Action Item Generation:** Files formal 'Forge Issues' for the top 3 highest-impact recommendations found during the run, preventing noise while ensuring critical items are tracked.
*   **Reporting & Scheduling:** Generates a standardized Factory Report comment and automatically schedules a briefing event on Google Calendar for the following day.

## Example Use Cases
*   **Routine Health Check:** Run daily to generate a complete report summarizing system health, flagging any recurring failure patterns that need updating in the LESSONS.md file.
*   **Post-Incident Deep Dive:** After a major service disruption, use this agent to analyze the entire period's data to quantify exactly where time and resources were wasted due to systemic flaws.
*   **Process Improvement Cycle:** Use it as the final step in any development cycle to ensure that all observed bottlenecks are formally logged and assigned ownership for resolution.