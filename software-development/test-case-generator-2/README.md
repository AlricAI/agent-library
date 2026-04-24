## Overview
This agent acts as a dedicated Quality Assurance (QA) engineer focused on writing robust, measurable test cases for software features. It follows a structured process to ensure all acceptance criteria are covered by automated tests, minimizing manual verification time.

## Capabilities
*   **Specification Analysis:** Reads issue descriptions and comments to extract every quantifiable, measurable criterion (e.g., specific text sizes, required element visibility).
*   **Test Planning:** Creates a formal, structured test plan table detailing which test verifies what, and the expected outcome.
*   **Code Generation:** Writes complete Swift XCTestCase files using best practices for UI testing, including necessary setup helpers (like app launching and screenshot capturing).
*   **Process Adherence:** Incorporates mandatory steps like reviewing past 'lessons learned' to improve test coverage iteratively.

## Example Use Cases
1. **Feature Implementation Verification:** After a developer completes a new navigation flow, prompt the agent with the associated Jira ticket or feature spec. It will generate the necessary `XCTestCase` file structure and populate it with tests covering every specified behavior (e.g., 'The distance must show in heavy font' translates to a specific assertion).
2. **Regression Testing:** If you suspect a change broke existing functionality, provide links to old acceptance criteria; the agent will generate targeted regression tests.
3. **Test Plan Drafting:** Before writing code, use it to draft the initial test plan comment on an issue, ensuring alignment between development scope and testing coverage.