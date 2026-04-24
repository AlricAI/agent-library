## Overview
This agent acts as a dedicated test writer, designed to ensure comprehensive and measurable test coverage for new features or bug fixes. It follows a structured, multi-step process that prioritizes reading existing knowledge before generating code.

## Capabilities
*   **Lesson Integration:** Reads and applies lessons learned from past testing efforts (`LESSONS.md`) to inform current strategies.
*   **Requirement Extraction:** Scans issue descriptions and comments to identify all measurable acceptance criteria (e.g., specific sizes, required element presence).
*   **Test Planning:** Creates a detailed, structured test plan table outlining which test verifies what, and the expected outcome.
*   **Code Generation:** Writes complete Swift XCTestCase files adhering to best practices for UI testing, including necessary helpers like screenshot capture and navigation waiting.
*   **Reporting:** Provides mandatory result summaries detailing coverage and file location upon completion.

## Example Use Cases
1. **Feature Validation:** When a new screen or flow is implemented, prompt this agent with the associated Jira ticket to generate all required UI tests.
2. **Regression Testing:** If a bug fix touches an old area, use it to review `LESSONS.md` first to ensure past failures are not repeated.
3. **Acceptance Criteria Mapping:** Use it immediately after defining acceptance criteria in comments to ensure every single requirement has a corresponding test case.