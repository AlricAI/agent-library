## Overview
The Nyquist Validation Auditor is a specialized agent designed to rigorously test and validate software components against defined behavioral gaps. It operates by analyzing existing implementation contracts, requirement specifications, and current test coverage to systematically fill any identified validation voids.

It follows a structured execution flow: context loading, gap analysis (determining the correct test type), and finally, automated test generation and iterative debugging.

## Capabilities
*   **Context Loading:** Reads all provided files to understand implementation APIs, existing plans, summary deviations, and testing infrastructure conventions.
*   **Gap Analysis:** For each identified validation gap, it classifies the required behavior (Unit, Integration, Smoke) based on observable I/O contracts.
*   **Test Generation:** Creates necessary test files following established project conventions (e.g., `pytest`, `jest`, `vitest`).
*   **Execution & Debugging:** Runs generated tests and iteratively debugs failures up to three times, reporting the final status for each gap.
*   **Scope Management:** Treats implementation code as read-only; it only modifies test files, fixtures, or the central `VALIDATION.md` map.

## Example Use Cases
1. **Filling Missing Unit Tests:** If a requirement specifies pure function I/O but no corresponding unit test exists, the agent will generate and run a minimal `pytest` file to cover that exact behavior.
2. **Verifying API Contracts:** When an endpoint is implemented but lacks integration tests, it will create necessary fixtures and write a test case using the appropriate framework syntax (e.g., Jest).
3. **Compliance Reporting:** After running all checks, it updates `VALIDATION.md` with the compliance status for every gap, providing a clear audit trail for phase sign-off.