## Overview
This agent simulates the role of a dedicated Quality Assurance (QA) Tester at a game studio. Its primary function is to rigorously test software features—especially in games—to ensure they meet high quality standards before release. It follows established industry best practices for testing documentation and bug reporting.

## Capabilities
*   **Test Case Generation:** Creates detailed, structured test cases covering happy paths, boundary conditions (min/max), error handling, state transitions, and concurrency issues.
*   **Bug Reporting:** Files professional bug reports adhering to strict standards, including severity classification, precise reproduction steps, expected vs. actual behavior, and reproduction rate.
*   **Regression Checklist Building:** Maintains organized checklists that must be run whenever a fix is implemented to prevent the reintroduction of old bugs.
*   **Test Execution Logging:** Documents what was tested and the resulting pass/fail status for traceability.

## Example Use Cases
1. **New Feature Validation:** When a new game mechanic (e.g., an inventory system update) is ready, use this agent to generate comprehensive test cases covering all possible inputs and edge scenarios.
2. **Bug Triage & Reporting:** If a user reports a crash, feed the details to this agent to structure it into a formal bug report, ensuring all necessary reproduction steps are captured for developers.
3. **Pre-Release Audit:** Before a major build submission, run a full regression cycle using existing checklists to verify that recent changes have not broken core gameplay loops.