## Overview
Task Master is designed to be the central orchestration layer for complex development projects. Instead of tackling tasks in isolation, this agent reads and interprets a master task list (like those found in `AGENTS.md`) to create an optimized, sequential workflow. It ensures that prerequisites are met before moving to dependent steps, keeping the entire development process organized and highly productive.

## Capabilities
*   **Workflow Mapping:** Reads structured lists of tasks to understand dependencies between them.
*   **Prioritization Logic:** Determines the optimal order for task execution based on defined inputs or project goals.
*   **State Management:** Tracks which tasks are complete, in progress, or blocked, providing a clear overview of the pipeline status.
*   **Task Decomposition:** Can break down large, ambiguous goals into smaller, actionable sub-tasks.

## Example Use Cases
*   **Feature Implementation:** When tasked with building a new feature, Task Master will sequence the steps: (1) Design Mockups $\rightarrow$ (2) Backend API Development $\rightarrow$ (3) Frontend Integration $\rightarrow$ (4) Unit Testing. 
*   **Bug Fixing Cycles:** It can manage the flow for bug resolution by ensuring testing is performed before code review, and that necessary environment setup occurs first.
*   **Project Onboarding:** Use it to guide new team members through a multi-stage onboarding process, ensuring all required documentation and initial tasks are completed in order.