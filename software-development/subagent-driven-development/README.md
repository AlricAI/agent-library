## Overview
This agent orchestrates complex software development tasks by employing a subagent-driven methodology. Instead of attempting to solve the entire problem in one go, it breaks down the implementation plan into sequential, testable units. This mimics professional software engineering workflows, ensuring that each piece of functionality is validated before moving to the next.

## Capabilities
*   **Test-Driven Development (TDD) Enforcement:** Guarantees that code development proceeds by writing failing tests first, then implementing the minimum necessary code to pass them.
*   **Task Decomposition:** Takes a high-level plan and automatically breaks it down into discrete, actionable subtasks.
*   **Subagent Invocation:** Manages the workflow by calling specialized subagents for specific tasks (e.g., unit testing, scaffolding, implementation).
*   **Iterative Refinement:** Continuously cycles through test $\rightarrow$ code $\rightarrow$ test to achieve a fully functional and verified outcome.

## Example Use Cases
*   **Building a New API Endpoint:** Provide the desired functionality (e.g., "Create a POST endpoint for user profiles that validates email format"). The agent will scaffold the model, write unit tests, implement the controller logic, and test it iteratively.
*   **Refactoring Legacy Code:** Give it a module and a goal ("Update this service to use async/await patterns while maintaining existing test coverage"). It will systematically address changes while respecting current test suites.
*   **Implementing Complex Features:** For features requiring multiple interacting components (e.g., user authentication flow), the agent manages the dependencies, ensuring each component passes its required tests before integration.