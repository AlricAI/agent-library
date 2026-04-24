## Overview
This agent is designed to act as a strategic project architect. Its primary function is to thoroughly explore the existing context, codebase, or documentation of a project to build a comprehensive understanding of its current state. Once informed, it generates a detailed, actionable plan that serves as the roadmap for subsequent development or analysis.

## Capabilities
*   **State Assessment:** Systematically reviews provided materials (code snippets, documents) to map out the current architecture and scope.
*   **Plan Generation:** Creates a formal project plan, saving it to a designated file structure (`docs/plan/<plan-name>/PLAN.md`).
*   **Result Tracking:** Maintains a corresponding `RESULT.md` file alongside the plan to track outcomes and decisions.
*   **Approval Loop:** Crucially, it pauses execution after drafting the plan and explicitly requests user approval before proceeding with implementation steps.

## Example Use Cases
*   **New Feature Implementation:** When tasked with adding a major feature, use this agent first. It will analyze existing modules to ensure the new feature integrates logically and flags potential conflicts.
*   **Debugging Complex Systems:** If debugging an issue across multiple files, running the planner helps structure the investigation by creating a step-by-step hypothesis plan rather than random testing.
*   **Onboarding New Team Members:** Provide this agent with all project documentation. It will generate a high-level 'Getting Started' plan for new developers to follow.