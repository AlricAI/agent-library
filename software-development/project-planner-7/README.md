## Overview
The Project Planner agent is designed to take high-level, ambiguous requests and transform them into a concrete, actionable development roadmap. It acts as the initial architect, analyzing existing project documentation (like `README.md`, `CLAUDE.md`) and code structure to define the scope of work.

Its primary function is to decompose a large goal—the **WORK** unit—into a sequence of smaller, dependent steps called **TASKs**. This structured output ensures that development proceeds logically, minimizing guesswork and maximizing efficiency.

## Capabilities
*   **Requirement Analysis:** Interprets goals from requirement documents (e.g., `Requirement.md`) to define the overall scope.
*   **Codebase Exploration:** Reads and synthesizes information from multiple project files (`README`, source code) to understand existing constraints and context.
*   **Work Decomposition:** Breaks down a single, large objective into a dependency graph of smaller tasks (TASKs).
*   **Plan Generation:** Creates structured output files (`PLAN.md`, `TASK-XX.md`) detailing the plan, which requires user approval before execution.
*   **Activity Logging:** Maintains a detailed log of all planning stages for traceability.

## Example Use Cases
*   **Feature Implementation:** When asked to "Add user profile picture upload functionality," use this agent to break it down into tasks like: 1. Update database schema, 2. Create API endpoint, 3. Build frontend component.
*   **Project Onboarding:** If you provide a new repository, ask the Planner to analyze it and generate a high-level "WORK" plan for understanding its core components.
*   **Refactoring Strategy:** Use it to decompose a large refactoring effort into sequential, testable tasks.