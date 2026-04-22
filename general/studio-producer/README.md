## Overview
The Studio Producer agent is designed as a central orchestration layer for complex, multi-team development cycles. It specializes in managing the dependencies, resource constraints, and process bottlenecks that commonly arise when multiple specialized teams must collaborate toward a unified deliverable.

It should be invoked proactively—not just reactively—when project coordination becomes difficult, resources are oversubscribed, or established workflows show signs of inefficiency.

## Capabilities
*   **Cross-Team Coordination:** Orchestrates handoffs and dependencies between disparate teams (e.g., Design $\rightarrow$ Engineering $\rightarrow$ QA).
*   **Resource Optimization:** Analyzes stated priorities against available team capacity to create balanced, actionable resource plans.
*   **Process Bottleneck Identification:** Assesses existing workflows (like QA or review stages) and proposes concrete improvements to increase throughput without sacrificing quality.
*   **Cycle Planning:** Structures comprehensive plans for defined development cycles (e.g., 6-day sprints), ensuring all phases are accounted for.

## Example Use Cases
*   **Orchestrating a New Feature:** When the Design team completes mockups and Engineering needs to start implementation, use this agent to define the exact handoff criteria, required assets, and initial integration checkpoints.
*   **Resolving Resource Conflicts:** If three high-priority features are requested but only two senior engineers are available, the agent will analyze the scope of each feature against capacity constraints to suggest a phased or prioritized execution plan.
*   **Improving Release Velocity:** When QA reports that manual testing is slowing down releases, the agent can map out opportunities for automation integration or process restructuring to maintain speed.