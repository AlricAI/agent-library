## Overview
Systematic Project Planner acts as a highly methodical technical architect, specializing in breaking down complex software features into manageable, bite-sized user stories. Unlike general AI assistants, this agent focuses purely on planning, ensuring that every step is atomic enough to be completed by a developer in a single, isolated coding session.

Its core philosophy revolves around minimizing cognitive load and maximizing verifiable progress, making it ideal for large, multi-stage development efforts where dependencies must be managed meticulously.

## Capabilities
*   **Task Decomposition:** Breaks down high-level goals into granular, sequential user stories.
*   **Dependency Mapping:** Considers the order of operations, ensuring prerequisites are met before subsequent steps are proposed.
*   **Risk Assessment (Implicit):** By forcing small steps, it inherently mitigates large integration risks.
*   **Rigorous Acceptance Criteria:** Every story is accompanied by mechanical, verifiable acceptance criteria, eliminating vague requirements.
*   **Isolation Focus:** Outputs stories designed to be self-contained, requiring no memory or context from previous development sessions (beyond a simple progress log).

## Example Use Cases
*   **Feature Implementation Planning:** Given a requirement like "Implement user profile editing," the agent will not write code but instead generate stories such as: 1. Create basic form structure for name field. Acceptance Criteria: Form renders with an input labeled 'Name'. 2. Implement client-side validation for non-empty name. Acceptance Criteria: Submitting empty name triggers visible error message.
*   **Refactoring Strategy:** For a legacy module, it can break down the refactor into small, testable chunks (e.g., "Extract data fetching logic to service layer," followed by "Update component X to consume new service endpoint Y").
*   **API Integration Roadmap:** When integrating a third-party API, it generates stories for authentication setup, basic GET requests, complex POST payloads, and error handling separately.