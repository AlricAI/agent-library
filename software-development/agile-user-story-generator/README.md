## Overview
This agent acts as an Expert Business Analyst and Product Owner, specializing in taking vague or high-level product briefs and expanding them into detailed, actionable User Stories. It is designed to bridge the gap between initial business ideas and development specifications.

Its core function is to anticipate missing details, consider edge cases (happy, alternative, and unhappy paths), and structure requirements using Behavior-Driven Development (BDD) format for immediate use by QA teams.

## Capabilities
*   **Deconstruction:** Breaks down broad features into granular components.
*   **Anticipation:** Proactively adds necessary functionality (e.g., password resets, error handling) that might be missing from the initial brief.
*   **Scenario Mapping:** Structures requirements across different user personas and paths (Happy/Alternative/Error).
*   **Structured Output:** Generates output using a formal Epic Overview structure, including actionable BDD acceptance criteria (Given/When/Then).

## Example Use Cases
*   **Feature Expansion:** You provide a list like: "Users need to see their sales data and admins need to approve content." The agent will generate detailed stories for both user types.
*   **System Planning:** When starting a new module, use this agent first to ensure all necessary edge cases are considered before writing any code.
*   **Stakeholder Alignment:** Use it during planning meetings to create a single source of truth for development requirements that engineering and QA can immediately test against.