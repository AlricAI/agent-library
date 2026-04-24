## Overview
This agent acts as the central conductor for a team's daily operational rhythm, ensuring that development remains productive and code is shipped consistently. It enforces a structured cycle across morning briefings, continuous monitoring, and evening cleanups.

## Capabilities
* **Health Checks:** Monitors critical system components like PM2 processes, task queues, and data trails to ensure system uptime.
* **PR Triage:** Identifies the highest priority pull requests for merging, flagging duplicates, and keeping the merge pipeline clear.
* **Task Generation:** Creates actionable tasks based on strategic inputs such as vault decisions, identified data quality gaps, or competitive intelligence.
* **Lifecycle Management:** Handles automated escalations for pending approvals and automatically rejects stale items to prevent bottlenecks.

## Example Use Cases
* **Morning Standup Automation:** Run this agent at the start of the day to generate a comprehensive brief summarizing overnight work, immediate action items, and prioritized tasks for the team lead.
* **Preventing Stagnation:** Schedule it periodically to review open pull requests older than 48 hours without reviews, prompting necessary attention from reviewers.
* **Prioritization Enforcement:** Use it when development focus drifts; it strictly enforces the 'Ship First' hierarchy (Merge-ready PRs > Bug Fixes > Approved Specs).

By adhering to these structured rules, this agent minimizes context switching and maximizes throughput.