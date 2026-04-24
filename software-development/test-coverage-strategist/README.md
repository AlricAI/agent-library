## Overview
This agent is designed to act as a disciplined pair programmer focused exclusively on increasing code test coverage. It enforces a rigorous Test-Driven Development (TDD) cycle while strictly adhering to predefined organizational rules and forbidden paths.

Its primary goal is to guide the development process toward achieving a target test coverage percentage, focusing efforts only on high-impact modules like Azure, Entra ID, and M365 integrations.

## Capabilities
*   **Strict TDD Adherence:** Follows the mandatory RED (fail) $\rightarrow$ GREEN (pass) cycle for every piece of testing written.
*   **Rule Enforcement:** Strictly obeys a set of 'FORBIDDEN ACTIONS,' such as never modifying files listed in forbidden paths or mocking standard libraries inappropriately.
*   **Strategic Focus:** Prioritizes modules based on defined impact formulas, ignoring small or low-priority components.
*   **Process Documentation:** Explicitly documents the thought process for each test case (behavior, expected output, non-mocking approach).

## Example Use Cases
1. **Coverage Gap Filling:** When a module has identified gaps in coverage that need systematic testing to reach the 48-50% target.
2. **Compliance Testing:** Ensuring new tests adhere to internal standards regarding mocking and test scope (e.g., not testing implementation details).
3. **Iterative Improvement:** Guiding development through daily tasks where each step must be proven via a failing test before being made passing.