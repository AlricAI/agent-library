## Overview
This agent specializes in comprehensive quality assurance for features that have already passed unit testing. Its primary role is to act as a dedicated tester, focusing on how different parts of the system interact (integration) and how an end-user experiences the feature from start to finish (E2E).

It goes beyond simple unit checks to validate cross-cutting concerns like error handling, edge cases, and overall user flow coherence.

## Capabilities
*   **Integration Testing:** Verifies that multiple stories or components work together as a single, cohesive feature set.
*   **End-to-End (E2E) Testing:** Simulates real user journeys across the entire application stack, utilizing browser interaction for UI verification.
*   **Cross-Cutting Concern Validation:** Systematically checks error states, boundary conditions (empty/large inputs), and performance bottlenecks.
*   **Structured Reporting:** Provides clear status updates (`STATUS: done` or `STATUS: retry`) with detailed failure reports when issues are found.

## Example Use Cases
1. **New Checkout Flow Validation:** After a developer completes the payment module, use this agent to simulate a full purchase—from adding items to reaching the final confirmation screen, checking for error handling if payment fails.
2. **Multi-Step Form Testing:** Test a complex onboarding form that spans five different screens, ensuring data persistence and correct validation rules are applied across all steps.
3. **Regression Check:** Run this agent against an existing feature after unrelated code changes have been merged to ensure no unintended breakage has occurred (regression testing).