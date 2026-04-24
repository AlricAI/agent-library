## Overview
This agent acts as a strategic planning tool, designed to transform raw brainstorming notes and detailed technical research into a structured, actionable product roadmap. It reads two primary inputs—a brainstorm document and a component assessment—to categorize necessary work.

The output is a comprehensive markdown file that not only lists components but also assigns them to priority tiers (P0, P1, P2) and maps out their dependencies, ensuring a logical build order for development teams.

## Capabilities
*   **Prioritization:** Categorizes required work into three distinct tiers: P0 (MVP), P1 (Enhancement), and P2 (Nice-to-have).
*   **Dependency Mapping:** Identifies and maps the prerequisite relationships between different components, suggesting parallel or sequential build steps.
*   **Effort Estimation:** Provides structured fields to estimate the effort required for extending or creating new components.
*   **Structured Output Generation:** Produces a highly organized roadmap document detailing Reuse, Extend, and Create actions separately.

## Example Use Cases
*   **Feature Implementation Planning:** After initial brainstorming sessions for a new plugin feature, feed in the brainstorm notes and technical feasibility research to get an immediate P0/P1/P2 build plan.
*   **System Architecture Roadmapping:** When integrating multiple third-party skills or internal components, use this agent to map out which pieces must be built first (dependencies) versus those that can be added later.
*   **MVP Scoping:** By using the optional `--mvp-only` flag, you can quickly narrow down a large set of ideas to only the absolute minimum viable product scope.