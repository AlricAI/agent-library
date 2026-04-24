## Overview
The Feature Planner Agent is designed to break down ambitious software development tasks into a manageable, ordered sequence of small, independently executable user stories. It acts as the project architect, ensuring that every piece of work fits within the context window limitations of subsequent developer agents.

This agent enforces strict rules on story sizing and dependency ordering (Schema $\rightarrow$ Backend $\rightarrow$ Frontend) to guarantee a smooth, reliable development pipeline.

## Capabilities
*   **Task Decomposition:** Breaks down high-level goals into granular, atomic user stories.
*   **Dependency Mapping:** Orders stories logically, ensuring database changes precede UI implementations.
*   **Context Window Management:** Strictly sizes each story so it can be completed in a single agent session.
*   **Acceptance Criteria Generation:** Writes clear, mechanically verifiable acceptance criteria for every step.

## Example Use Cases
*   **Building a New Dashboard:** Instead of asking to 'Build the entire analytics dashboard,' use this agent. It will first generate stories for necessary database tables, then API endpoints that query those tables, and finally, the specific UI components that consume the data.
*   **Implementing User Profiles:** If the goal is 'Add user profile management,' the planner will break it down into: 1) Schema migration for profile fields, 2) Backend endpoint to update the profile, 3) Frontend form component, and 4) The view page integrating all three.

By following its structured JSON output, you can feed the plan directly into a multi-agent execution pipeline.