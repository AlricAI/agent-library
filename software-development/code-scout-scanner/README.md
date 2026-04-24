## Overview
Code Scout Scanner is an advanced agent designed to perform comprehensive gap analysis on mobile application codebases. Its primary function is to systematically cross-reference declared UI elements (like accessibility identifiers) against existing unit and UI test suites to pinpoint areas lacking adequate testing coverage.

This tool follows a multi-step, structured process, ensuring that both the presence of an element and its expected state are verified across all relevant components.

## Capabilities
*   **Accessibility ID Inventory:** Scans core application directories via SSH to list all defined `accessibilityIdentifier` calls.
*   **Test Assertion Scanning:** Greps through UI test files (`.swift`) to inventory existing assertions, looking for `.exists`, `XCTAssert`, and specific element checks.
*   **Gap Detection:** Cross-references the inventories to identify accessibility IDs that are declared but never tested.
*   **State Coverage Check:** Verifies if tests adequately cover both positive (`.exists`) and negative (`!element.exists`) states for navigational elements.
*   **Data Accuracy Flagging:** Flags instances where tests only check for existence without validating specific data points (e.g., checking presence but not the actual speed value).
*   **Screen Coverage Mapping:** Lists all view/component files and compares them against existing test suites to identify entirely untested screens.

## Example Use Cases
1. **Pre-Release Audit:** Run this agent before a major release cycle to generate a comprehensive report detailing every UI element that needs a corresponding test case written.
2. **Feature Parity Check:** After adding a new screen or component, run the scan to ensure all newly added elements have been accounted for in the testing matrix.
3. **Test Suite Refactoring:** Use the output to guide developers on which existing tests need updating (e.g., changing from checking only `.exists` to validating specific labels).

By following its mandatory 'Lessons Learned' protocol, this agent continuously improves its scanning logic based on past successful and failed analyses.