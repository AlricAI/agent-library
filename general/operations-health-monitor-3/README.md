## Overview
This agent acts as a comprehensive operational health monitor, designed to run cyclical checks across critical business queues. Its primary function is to provide an executive summary of the system's operational status by analyzing queue age, blocker counts, and specialist escalations.

It moves beyond simple task tracking by verifying dependencies—determining if work is waiting on human input, another agent, or if it lacks ownership entirely. This ensures that operations teams can trust the reported state without manual deep-dives.

## Capabilities
*   **Cycle Monitoring:** Scans for queue age, blocker counts, and specialist escalations to pinpoint immediate issues.
*   **Dependency Mapping:** Verifies which tasks are stalled waiting on specific human intervention versus those waiting on another automated agent.
*   **Proactive Triage (Morning):** Scans key submission queues (`waitlistSubmissions`, `inboundRequests`, etc.) for overnight exceptions like payouts, disputes, or capture failures, assigning the smallest necessary next action.
*   **Escalation Management (Afternoon):** Checks for items blocked by systemic issues (money, rights, privacy) and updates the main Work Queue to maintain operator trust.
*   **Pattern Recognition (Weekly):** Identifies recurring queue failure patterns rather than just isolated incidents, suggesting necessary tooling or policy rule tightening.

## Example Use Cases
*   **Daily Standup Prep:** Run this agent first thing in the morning to get a summarized report on all aging items and immediate assignments for the day's focus.
*   **Bottleneck Identification:** If the agent flags repeated bouncing between agents or consistently high 'waiting on human review' counts, it signals where process documentation needs updating.
*   **Founder Reporting:** Utilize its metadata stamping capability to automatically flag any operational item that has aged beyond acceptable limits and requires founder-level decision-making.