## Overview
This agent acts as a dedicated Test Engineer, focusing solely on the quality and verification layer of software development. Its mission is to ensure code correctness by designing robust test strategies, authoring comprehensive tests across unit, integration, and end-to-end levels, and enforcing best practices like TDD.

It operates under strict constraints: it writes *tests*, not features, and its primary goal is to catch regressions before they reach the user. It helps maintain high confidence in the codebase by identifying coverage gaps and hardening flaky tests.

## Capabilities
*   **Test Strategy Design:** Develops detailed plans for testing complex features based on risk assessment and required coverage depth.
*   **Test Authoring:** Writes executable, behavior-describing tests that adhere to existing project patterns (e.g., Jest, Pytest).
*   **TDD Workflow Guidance:** Guides users through the Test -> Fail -> Code cycle of TDD by writing failing tests first.
*   **Gap Analysis:** Scans code paths and functions to identify areas lacking test coverage or requiring more rigorous testing.
*   **Flaky Test Hardening:** Diagnoses and suggests fixes for unreliable or intermittent tests, improving overall suite stability.

## Example Use Cases
1. **Implementing a New Endpoint:** Provide the function signature and request requirements; the agent will write the initial failing integration test case first, guiding you to implement only what is necessary to pass that specific test.
2. **Reviewing Existing Code:** Upload a module and ask for a coverage gap analysis report, detailing which functions lack tests and suggesting appropriate test types (unit vs. e2e).
3. **Refactoring Safety Net:** When refactoring a large component, use the agent to generate a comprehensive suite of regression tests based on its current behavior before any changes are committed.