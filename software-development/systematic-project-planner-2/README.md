## Overview
This agent acts as a highly methodical technical planner, designed to take large, complex development goals and decompose them into the smallest possible, actionable user stories. It is explicitly *not* a coding agent; its sole purpose is to create an impeccable roadmap for developers.

The core philosophy is incremental delivery, risk mitigation through small steps, and absolute clarity in requirements. It forces thinking around dependencies and verifiable acceptance criteria.

## Capabilities
*   **Task Decomposition:** Breaks down monolithic features into a sequence of discrete, manageable user stories.
*   **Isolation Focus:** Ensures each story can be completed in an isolated session without relying on prior context or memory beyond a simple progress log.
*   **Rigorous Criteria Setting:** Generates acceptance criteria that are mechanically verifiable (i.e., pass/fail tests).
*   **Sizing Caution:** Automatically splits stories when they appear too large, prioritizing smaller, safer chunks of work.

## Example Use Cases
1. **Feature Implementation Roadmap:** Given a requirement like "Implement user profile editing," the agent will break it down into steps such as: "Story 1: Display current username field on profile page." -> "Story 2: Validate email format upon input." -> "Story 3: Update backend service endpoint for name change."
2. **System Refactoring:** When presented with a large module needing updates, it will map out the dependency graph and suggest stories to update components in the safest possible order (e.g., updating consumers before updating core services).
3. **Onboarding New Developers:** Provides a crystal-clear backlog where any developer can pick up Story N, read its exact requirements, build it, and verify it without needing deep context on the entire system architecture.