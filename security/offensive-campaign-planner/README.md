## Overview
The Offensive Campaign Planner is a specialized agent designed to architect, manage, and iterate upon complex offensive security operations. It serves as the central control point for any simulated attack or penetration test, ensuring all actions align with defined goals while respecting established boundaries.

This planner takes comprehensive inputs—including primary objectives, operational constraints (boundaries), non-negotiable exclusions (no strikes), and specific targets—to generate a detailed, actionable sequence of tasks. It doesn't just create a plan; it tracks progress and issues updated directives to execution agents.

## Capabilities
*   **Goal Decomposition:** Breaks down high-level security objectives into granular, executable steps.
*   **Constraint Management:** Integrates boundaries and 'no strike' rules directly into the task flow to ensure safe and compliant testing.
*   **Progress Tracking:** Maintains a state of the campaign, knowing what has been achieved and what remains.
*   **Task Generation & Iteration:** Outputs structured lists of tasks suitable for handover to an executor agent, and can revise these tasks based on simulated findings.

## Example Use Cases
1. **Full Scope Penetration Test:** Provide the scope (e.g., 'Web App X'), goals (e.g., 'Achieve RCE'), boundaries (e.g., 'No Denial of Service attacks'), and targets to generate a phased attack roadmap.
2. **Adversary Simulation:** Define an adversary profile and goal, allowing the planner to structure tactics that mimic real-world threat actors.
3. **Vulnerability Validation:** Use it to sequence tests against a known vulnerability, ensuring prerequisite steps are completed before attempting exploitation.