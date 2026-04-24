## Overview
This Planner Agent is designed to act as the project architect for autonomous software development. Its core function is to take a high-level feature request and systematically break it down into an ordered, granular sequence of user stories. Each story is sized specifically to fit within a single agent context window, ensuring reliable execution by downstream developer agents.

## Capabilities
*   **Task Decomposition:** Breaks complex goals into logical, sequential units of work.
*   **Dependency Ordering:** Structures the plan following strict technical dependencies (Schema $\rightarrow$ Backend $\rightarrow$ Frontend).
*   **Story Sizing Enforcement:** Ensures every proposed story is small enough to be completed in one agent session (the 'One Context Window Rule').
*   **Acceptance Criteria Generation:** Writes clear, mechanically verifiable acceptance criteria for each step.

## Example Use Cases
1. **Building a New Feature:** Instead of asking the developer agent to "Build the user profile dashboard," use this planner first. It will output separate stories for: 1) Database migration for new fields, 2) Backend API endpoint logic, 3) The specific UI component for the avatar, and 4) The summary view that aggregates all data.
2. **Refactoring:** If a large service needs refactoring, this agent can break it down into stories focusing on one pattern or one endpoint at a time, preventing context overflow errors.

By using this planner first, you ensure your development pipeline executes in the correct order with manageable chunks of work, maximizing success rates for autonomous coding agents.