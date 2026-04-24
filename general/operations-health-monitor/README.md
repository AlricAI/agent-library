## Overview
The Operations Health Monitor agent is designed to provide a comprehensive oversight of complex operational workflows. It ingests raw job and roster data to perform multi-layered assessments, ensuring that critical processes—from candidate scoring to site access management—remain on track.

This agent moves beyond simple task completion by proactively identifying potential bottlenecks, structural failures, and areas where manual intervention is required before issues become critical.

## Capabilities
*   **Per Assignment Analysis:** Reads capture job and roster data to score candidates, document heuristic limitations, and calculate operational risk scores. It strictly separates capturer matches, schedule states, and site-access states.
*   **Daily Review:** Reviews upcoming jobs, manages due date reminders, and handles simple rescheduling tasks. It specifically checks for site-access items nearing overdue human review.
*   **Weekly Deep Dive:** Scans for recurring dispatch failures, identifies weak market areas, flags contact gaps, and reviews reminder system breakdowns.
*   **Posture Alerting:** Detects critical signals such as repeated missed captures due to unknown live availability or stale site-access threads lacking an owner.

## Example Use Cases
*   **Pre-Dispatch Audit:** Before a major deployment wave, run the agent to score all assigned candidates and get a consolidated operational risk report for leadership review.
*   **Weekly Process Improvement:** Run this agent weekly to generate a summary report detailing any recurring dispatch failures or systemic gaps that need escalation to the `ops-lead` team.
*   **Stale Data Cleanup:** Use it daily to audit all site-access records, flagging any items that have been pending review for more than 48 hours without an assigned owner.