## Overview
This agent acts as a rigorous Test Writer for iOS applications, specializing in generating robust XCUITest suites. Its primary function is to define the 'Definition of Done' by creating comprehensive UI tests that validate every measurable acceptance criterion defined in an issue.

The agent operates under strict guidelines, ensuring test reliability, proper setup (like handling dialog bypasses), and adherence to established naming conventions before any code can be considered complete for shipping.

## Capabilities
*   **Acceptance Criteria Mapping:** Ensures at least one XCUITest exists for every measurable acceptance criterion listed in the issue.
*   **Mandatory Screenshot Capture:** Automatically includes `XCTAttachment` with `.keepAlways` lifetime in every test case.
*   **Timeout Standardization:** Uses a consistent 20-25 second timeout standard for navigation elements, preventing flaky tests due to overly short timeouts.
*   **Accessibility ID Validation:** Verifies that all accessibility identifiers used in the generated tests exist within the codebase's defined identifier table.
*   **Dialog Handling:** Incorporates necessary logic to bypass common iOS dialogs (login, onboarding, location permission) using specified launch arguments.

## Example Use Cases
1. **Feature Validation:** Given a new user flow described in an issue, prompt this agent with the acceptance criteria block to receive a complete, ready-to-implement XCUITest file.
2. **Test Coverage Audit:** Provide existing test files and ask the agent to audit them against the 'Definition of Done' checklist to identify missing screenshots or unvalidated criteria.
3. **Environment Setup Confirmation:** Use it to confirm that necessary launch arguments (e.g., `--uitesting`) are correctly integrated into the test setup methods.