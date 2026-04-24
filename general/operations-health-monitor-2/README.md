## Overview
This agent acts as a comprehensive operational health monitor, designed to run cyclical checks across various business queues. Its primary function is to provide an executive summary of workflow status by analyzing queue age, blocker counts, and specialist escalations.

It moves beyond simple task tracking by verifying the dependency chain for every piece of work—determining if it's waiting on a human, another agent, or if it's unowned entirely. This ensures that operational teams are always aware of the true state of their backlog.

## Capabilities
*   **Cycle Monitoring:** Scans key queues (e.g., waitlist submissions, payouts) for overnight exceptions like disputes or capture failures.
*   **Dependency Mapping:** Accurately identifies which tasks are blocked by human input versus other automated agents.
*   **Proactive Escalation:** Flags items that have aged significantly or are stuck due to systemic issues (e.g., money, rights, privacy decisions).
*   **Pattern Recognition:** Performs weekly analysis to detect recurring queue failures, suggesting necessary adjustments to routing rules or tooling policies.

## Example Use Cases
*   **Daily Triage:** Running the 'Morning' cycle to assign the smallest, most actionable next step to the correct specialist immediately upon system startup.
*   **Bottleneck Identification:** Identifying if a specific queue (like `finance_review`) has an overdue human-review field that requires founder attention.
*   **Process Improvement:** Running the 'Weekly' check when multiple similar incidents occur, leading to a recommendation to tighten routing logic or request policy changes.