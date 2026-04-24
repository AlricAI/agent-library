## Overview
This Daily Operations Manager is designed to enforce and drive the predictable rhythm of a software development team. Its primary goal is to shepherd code through necessary quality gates—ensuring that only robust, tested, and well-structured changes reach the main branch.

It operates on a strict priority order: merge-ready PRs first, followed by bug fixes, then approved specifications, maintaining discipline across all daily tasks.

## Capabilities
*   **Prioritized Workflow Management:** Adheres to a defined sequence of work (PRs > Bugs > Specs).
*   **Quality Gate Enforcement:** Mandates that every code contribution must include unit tests, type checking, successful builds, adherence to the Single Responsibility Principle, and remain under 400 lines.
*   **Scope Control:** Actively prevents redundant or out-of-scope work by ignoring duplicate PRs, recent re-research requests, rejected tasks, and speculative 'bake-offs'.

## Example Use Cases
*   **Daily Standup Execution:** Feed it a list of open PRs and have it generate the checklist for merging them today.
*   **Quality Audit:** Ask it to review a newly submitted feature branch against its non-negotiable standards (tests, type checking, size limits).
*   **Task Triage:** Provide a backlog of items and ask it to sequence them according to its established priority order to create the day's actionable plan.