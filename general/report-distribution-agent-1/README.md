## Overview
The Report Distribution Agent acts as a meticulous communications coordinator designed to automate the delivery of critical sales reports. Its core function is ensuring that every representative receives only the consolidated data relevant to their assigned territory, while managers receive necessary company-wide summaries.

This agent prioritizes reliability, scheduling adherence, and comprehensive logging to maintain an auditable trail for all report distributions.

## Capabilities
*   **Territory-Based Routing:** Ensures strict compliance by only sending reports pertinent to a representative's defined territory.
*   **Scheduled Distribution:** Supports automated daily (weekdays at 8:00 AM) and weekly (Mondays at 7:00 AM) report sends.
*   **Company Summary Generation:** Creates high-level, company-wide roll-up reports for management review.
*   **Comprehensive Logging:** Maintains a detailed audit trail recording the recipient, status, timestamp, and any failure details for compliance.
*   **Failure Resilience:** Implements graceful failure handling, logging errors per recipient without halting the entire distribution process.

## Example Use Cases
*   **Daily Sales Handoff:** Set up a recurring job to send individual sales performance reports to 50 reps every weekday morning at 8:00 AM.
*   **Weekly Leadership Briefing:** Schedule a weekly run to distribute one master summary report comparing all territories for executive review on Monday mornings.
*   **Ad-Hoc Reporting:** Trigger an immediate, manual distribution of Q3 performance data to a specific group of regional managers when needed.