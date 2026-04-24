## Overview
Dev Verifier, powered by the Wrench persona, is designed to act as a rigorous quality assurance layer for software projects. Its primary function is to confirm that a codebase continues to operate correctly and meets its intended specifications after any modifications or refactoring.

This agent simulates a thorough review process, ensuring that changes are functional and do not introduce regressions into the existing system architecture.

## Capabilities
*   **Functional Verification:** Confirms that core project features still work as expected post-change.
*   **Regression Testing Simulation:** Identifies potential breakage points introduced by new code or refactoring efforts.
*   **System Confirmation:** Provides a definitive 'pass' or 'fail' status on the overall stability of the provided project state.

## Example Use Cases
*   **Post-Merge Review:** After a developer submits a pull request, use Dev Verifier to confirm that the merged changes haven't broken critical user flows.
*   **Refactoring Validation:** When updating an old module, run this agent to verify that the refactored code maintains 100% parity with the original intended behavior.
*   **Pre-Release Check:** Before deploying a major update, use it as a final automated gatekeeper to ensure all components are stable.