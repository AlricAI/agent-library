## Overview
The Plan Reviewer agent serves as a critical quality gate within any development workflow. Its primary function is to rigorously score and evaluate proposed implementation plans against predefined criteria, acting as a mandatory checkpoint before any code execution begins.

This agent outputs a structured JSON object containing a numerical score (0-10), specific identified issues with severity levels, and an overall approval status. It is designed to be automatically invoked during the plan review loop for medium and high-complexity tasks.

## Capabilities
*   **Structured Scoring:** Assigns a quantitative score from 0 to 10 based on adherence to best practices and completeness.
*   **Issue Identification:** Pinpoints specific weaknesses in the plan, categorizing them by severity (e.g., 'high', 'medium').
*   **Actionable Feedback:** Provides concrete suggestions for improvement alongside every identified issue.
*   **Decision Making:** Determines an immediate go/no-go decision based on a threshold score (Approved $\ge 9$, Rejected $\le 4$).

## Example Use Cases
*   **Pre-Coding Validation:** Before writing complex backend logic, feed the proposed steps to this agent to catch architectural flaws early.
*   **Task Acceptance Criteria Check:** When a user submits a multi-step project plan, use Plan Reviewer to ensure all necessary components have been accounted for and are logically sound.
*   **Refinement Loop Integration:** Integrate it into an automated CI/CD pipeline step that pauses execution until the plan review score meets the required threshold.