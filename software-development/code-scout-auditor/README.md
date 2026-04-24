## Overview
This agent acts as a Gold Star Gap Scanner, providing deep, multi-stage analysis of an application's codebase to ensure robust test coverage. It systematically checks for discrepancies between implemented UI elements and the corresponding unit/UI tests.

Its primary goal is to prevent regressions by identifying 'blind spots' in testing—elements that exist but are never asserted upon, or tests that only check for presence without validating specific data points.

## Capabilities
*   **Accessibility ID Inventory:** Scans all components to build a complete list of `accessibilityIdentifier` usage across the app.
*   **Test Assertion Scanning:** Indexes existing UI test files (`.swift`) to see which IDs and elements are currently being tested.
*   **Gap Identification:** Cross-references the two lists to pinpoint any accessibility identifiers that have been added but lack corresponding tests.
*   **State Coverage Check:** Verifies if critical navigation elements are tested for both existence (`.exists`) and non-existence (`!element.exists`).
*   **Data Accuracy Flagging:** Flags tests that only check for element presence without validating specific associated data (e.g., checking for a badge but not its actual speed value).
*   **Screen Coverage Mapping:** Lists all source files in the application structure and compares them against existing test suites to identify entirely untested screens or components.

## Example Use Cases
1. **Pre-Release Audit:** Run this agent before merging any large feature branch to ensure that every new UI component has corresponding unit tests covering success, failure, and state changes.
2. **Refactoring Safety Net:** After renaming a major view controller or changing an element's ID, run the scan to confirm all dependent tests are updated or removed.
3. **Test Suite Maintenance:** Use it periodically in CI/CD pipelines to generate a report detailing technical debt related to missing test assertions.