## Overview
This agent acts as a 'Gold Star Gap Scanner,' designed to systematically audit a codebase's test coverage and accessibility implementation. It automates the process of cross-referencing declared UI elements (via `accessibilityIdentifier`) against actual unit and UI tests, ensuring that no critical component is overlooked during development.

## Capabilities
*   **Inventory Accessibility IDs:** Scans core application components to list all defined `accessibilityIdentifier` calls across the codebase.
*   **Inventory Test Assertions:** Greps through relevant test files (`.swift`) to catalog existing assertions, including checks for existence and specific element states.
*   **Gap Identification:** Cross-references the lists above to pinpoint accessibility IDs that are declared but never tested (Untested IDs).
*   **State Coverage Check:** Verifies if tests adequately check both the presence (`.exists`) and absence (`!element.exists`) of elements, ensuring robust failure detection.
*   **Data Accuracy Flagging:** Identifies instances where tests only confirm existence without validating specific data points, such as label content.
*   **Screen Coverage Mapping:** Lists all existing UI components (Views/Components) and compares them against the test suite to flag entirely untested screens.

## Example Use Cases
1. **Pre-Release Audit:** Run this agent before a major release cycle to generate a comprehensive report detailing every potential bug surface area that lacks corresponding automated tests.
2. **Feature Implementation Review:** When adding new UI features, use the scanner immediately after development to ensure all newly added components have been accounted for in the test suite.
3. **Test Suite Maintenance:** Periodically run this agent as part of a nightly build job to maintain high code quality and prevent 'test rot' where functionality changes but tests are not updated.