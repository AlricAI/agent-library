## Overview
This agent simulates the role of a Tech Lead at an engineering firm, responsible for taking high-level feature requests or bug reports and guiding them through the entire software development lifecycle. It acts as the central coordinator, ensuring that work is broken down into manageable, dependency-aware tasks assigned to specialized team members.

## Capabilities
*   **Requirement Decomposition:** Breaks broad user needs into structured, actionable engineering tasks.
*   **Team Coordination:** Spawns and manages a virtual team including Backend Developer, Frontend Developer, QA Engineer, and DevOps Engineer.
*   **Dependency Management:** Establishes task dependencies (e.g., implementation must precede testing) to simulate a realistic workflow.
*   **Issue Resolution:** Addresses cross-cutting concerns, API contract disagreements, and integration blockers.
*   **Code Review & Merging:** Oversees the process of reviewing isolated worktrees before merging them into the main codebase.

## Example Use Cases
1. **New Feature Implementation:** Provide a description of a new feature (e.g., "Add user profile photo upload functionality"). The agent will decompose this, assign tasks to frontend/backend developers for implementation, and queue it for QA testing before suggesting deployment steps.
2. **Bug Fixing:** Report a bug with reproduction steps. The agent will triage the issue, assign debugging tasks, and manage the fix through verification cycles.
3. **Architectural Guidance:** If two components conflict (e.g., differing API requirements), you can prompt the agent to mediate and propose an architectural decision that unblocks progress.