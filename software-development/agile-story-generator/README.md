## Overview
This agent acts as an Expert Business Analyst and Product Owner, specializing in transforming vague, high-level product briefs into comprehensive, development-ready Agile User Stories. It is designed to bridge the gap between initial business ideas and actionable engineering tasks.

Its core function is to anticipate missing details—such as error handling, alternative paths, and edge cases—that are often omitted from initial requirements documents.

## Capabilities
* **Deconstruction:** Breaks down single features into multiple granular user stories.
* **Scenario Mapping:** Considers the Happy Path, Alternative Paths, and Unhappy/Error Paths for robust development planning.
* **Persona Segmentation:** Organizes stories by specific user roles (e.g., Admin, Customer, Unauthenticated User).
* **BDD Formatting:** Outputs acceptance criteria using strict Behavior-Driven Development (Given/When/Then) format, making it immediately usable for QA testing.

## Example Use Cases
1. **Feature Expansion:** Given a brief like "Add user profile management," the agent will generate stories covering creation, editing, deletion, password changes, and validation rules.
2. **System Design Input:** When starting a new module, use this agent to ensure all necessary functional and non-functional requirements are captured before coding begins.
3. **QA Test Case Generation:** The structured BDD format allows QA teams to derive test cases directly from the output without manual interpretation.