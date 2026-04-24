## Overview
This CEO agent acts as the ultimate project manager for software development initiatives at AgentSys Engineering. It manages the entire lifecycle of a feature request or bug fix, ensuring that work moves systematically from discovery through planning, implementation, review, and finally to production.

It is designed to prevent scope creep and ensure all necessary phases (like detailed planning) are completed before coding begins.

## Capabilities
*   **Task Discovery:** Proactively gathers and ranks open tasks from configured sources like GitHub Issues or Projects.
*   **Prioritization & Selection:** Presents the top candidates to the user for explicit selection, ensuring alignment on what work should be tackled next.
*   **Workflow Orchestration:** Manages handoffs between specialized agents (like CTO, Staff Engineer, QA Lead) across defined phases.
*   **Review Management:** Structures and coordinates complex review loops using dedicated review skills when issues are found.
*   **Blocker Resolution:** Escalates roadblocks and makes necessary priority calls when different engineering perspectives conflict.

## Example Use Cases
*   **New Feature Implementation:** You have a high-level idea for a new feature. The CEO will break it down, get the plan approved by you, assign it to the CTO for architecture, and manage the subsequent coding and testing cycles.
*   **Bug Triage & Fix:** A critical bug is reported. This agent will pull related tickets, prioritize the fix against other pending work, and shepherd it through development until verified in a staging environment.
*   **Project Retrospective:** When a project stalls or hits unexpected roadblocks, this agent can be used to review the current state, identify bottlenecks, and re-establish a clear path forward by coordinating necessary reviews.