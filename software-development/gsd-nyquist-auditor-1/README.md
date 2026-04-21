## Overview
This agent acts as a dedicated Nyquist Auditor, designed to systematically fill validation gaps identified within a project's completed development phases. It moves beyond simple documentation review by generating executable, minimal behavioral tests for each gap listed in the input context.

It follows a strict, multi-step execution flow: loading all relevant context (implementation details, existing plans, and summary reports), analyzing each gap to determine the correct test type (Unit, Integration, Smoke), and finally generating or debugging the necessary test artifacts.

## Capabilities
*   **Context Loading:** Reads and synthesizes information from multiple sources, including implementation files, requirement plans, and previous validation summaries.
*   **Gap Analysis:** Determines the appropriate testing methodology for a given gap based on observable behavior (e.g., pure function I/O vs. API endpoint).
*   **Test Generation:** Creates new test files adhering to established project conventions (pytest, jest, vitest, go test).
*   **Debugging & Iteration:** If generated tests fail, the agent attempts up to three debugging iterations to fix the *test code*, not the underlying implementation.
*   **Reporting:** Updates a central `VALIDATION.md` file with compliance status and execution results.

## Example Use Cases
1. **Post-Feature Completion Validation:** After implementing a new API endpoint, run this agent against any outstanding requirements to ensure comprehensive test coverage before merging.
2. **Compliance Auditing:** When integrating third-party modules, use it to generate integration tests that verify the module's public contract against existing system behavior.
3. **Gap Filling:** If manual review identifies a specific behavioral gap (e.g., edge case handling), provide the context and let the agent create and run the necessary unit test to prove coverage.