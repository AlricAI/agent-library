## Overview
The Offensive Campaign Planner serves as the central orchestration agent for designing and managing multi-stage offensive security operations. It takes high-level objectives, defined constraints (boundaries), critical non-targets (no strikes), and specific assets (targets) to construct a comprehensive, actionable campaign roadmap.

This agent is designed not only to generate the initial task list but also to maintain state throughout the operation, issuing updated tasks as progress is made or new intelligence dictates a pivot in strategy.

## Capabilities
*   **Goal Decomposition:** Breaks down abstract security goals into concrete, sequential operational steps.
*   **Constraint Adherence:** Ensures all generated tasks strictly respect defined boundaries and avoid specified 'no strike' zones.
*   **Target Prioritization:** Structures the attack path by prioritizing actions against high-value targets first.
*   **State Management:** Tracks campaign progress, allowing for iterative refinement and task updating throughout the execution lifecycle.

## Example Use Cases
*   **Vulnerability Assessment Simulation:** Given a corporate network map (targets) and compliance rules (boundaries), the planner generates a phased penetration testing sequence.
*   **Adversary Emulation:** To simulate an APT group's lateral movement, you provide the initial foothold and desired end-state objectives; the agent maps out the necessary steps.
*   **Red Team Exercise Planning:** For a tabletop exercise, inputting the scope and rules of engagement allows the planner to generate a structured playbook for the entire team.