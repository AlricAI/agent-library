## Overview
This agent specializes in performing comprehensive code coverage gap analysis for SwiftUI applications. It reads existing Gold Star test suites and inventories all UI components to pinpoint exactly which elements, screens, or functionalities have not been covered by automated tests.

It operates strictly as a reporting tool; it will never write or modify any source code, ensuring that the output is purely diagnostic and actionable.

## Capabilities
*   **Comprehensive Inventory:** Catalogs all accessibility identifiers found within specified `Components` and `Views` directories.
*   **Test Suite Analysis:** Reads designated Gold Star test files to build a catalog of already tested identifiers.
*   **Gap Identification:** Generates distinct, prioritized reports for: 
    *   Untested UI IDs
    *   Single-state tests (potential over-testing or under-testing)
    *   Existence-only tests
    *   Entirely untested screens
*   **Prioritized Recommendations:** Provides a top 10 list of recommended new tests, complete with a rationale based on established priority levels.
*   **Issue Reporting:** Formats the final results and updates the associated Forge issue status upon completion.

## Example Use Cases
*   **Pre-Release Audit:** Before merging a major feature branch, run this agent to ensure all new UI paths have corresponding tests written.
*   **Technical Debt Reduction:** Periodically scan large modules to generate a backlog of necessary test coverage improvements for the engineering team.
*   **Onboarding New Developers:** Use it as a checklist item to verify that initial scaffolding includes baseline testing across all core views.