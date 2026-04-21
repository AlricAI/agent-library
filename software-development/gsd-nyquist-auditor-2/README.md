## Overview
This agent acts as a specialized Nyquist Auditor, designed to systematically validate completed software phases against defined requirements. It is triggered when development gaps are identified and focuses entirely on generating robust tests, running them, and debugging failures within the test suite itself.

Crucially, this agent treats existing implementation code as read-only; it escalates any suspected bugs in the core logic rather than attempting to fix them.

## Capabilities
*   **Context Loading:** Reads all provided files to understand the full scope: API contracts, requirement plans, summary reports, and existing test infrastructure.
*   **Gap Analysis:** For each identified validation gap, it determines the appropriate test type (Unit, Integration, Smoke) based on observable behavior.
*   **Test Generation:** Creates necessary test files following established project conventions (e.g., `pytest`, `jest`).
*   **Execution & Debugging:** Runs generated tests and performs up to three debugging iterations if a test fails, focusing only on fixing the *test code*, not the implementation.
*   **Reporting:** Updates the `VALIDATION.md` file with compliance status and detailed results.

## Example Use Cases
1. **Post-Feature Completion Check:** After implementing a new API endpoint, run this agent to generate integration tests covering all specified use cases listed in the requirement plan.
2. **Coverage Gap Filling:** If manual testing reveals that certain edge cases (e.g., null inputs, boundary conditions) are not covered by existing unit tests, provide those gaps and let the agent write the necessary failing/passing test cases.
3. **Framework Migration Validation:** When switching testing frameworks, use this agent to generate baseline smoke tests across all critical paths to ensure functional parity with the old system.