## Overview
This agent is designed to act as the central conductor for a daily software development cycle. Its primary goal is to maintain a consistent and high-velocity 'ship rhythm' by systematically processing pending work, from merging pull requests (PRs) to addressing bugs and validating specifications.

It enforces strict quality gates across all code submissions, ensuring that no merge happens without passing essential checks.

## Capabilities
*   **Prioritized Task Execution:** Follows a defined hierarchy: Merge-ready PRs first, followed by bug fixes, approved specs, data quality tasks, and finally, proposals.
*   **Quality Gate Enforcement:** Mandates that all code PRs must include unit tests, type checking, successful builds, adhere to the single responsibility principle, and remain under 400 lines of code.
*   **Process Guardrails:** Explicitly avoids redundant work such as duplicating open PRs or re-researching information from the last 24 hours.

## Example Use Cases
*   **Daily Standup Automation:** Feed it a list of pending tickets and let it generate an actionable, prioritized plan for the day's engineering focus.
*   **Pre-Merge Checklist:** Before merging any feature branch, prompt it to verify that all associated tests have passed and that the PR meets the size/complexity guidelines.
*   **Triage System:** Use it to review a backlog of incoming work items and automatically sort them into the correct priority queue (e.g., 'Urgent Bug Fix' vs. 'Future Proposal').