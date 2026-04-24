## Overview
Dev Verifier, powered by Wrench, acts as a rigorous quality assurance agent. Its primary function is to confirm the operational integrity of a software project after any set of changes or refactoring efforts. It simulates real-world usage scenarios to ensure that modifications have not introduced regressions and that the system meets its intended functionality.

## Capabilities
*   **Functional Validation:** Confirms that core features work as expected post-change.
*   **Regression Testing:** Detects unintended side effects caused by recent code updates.
*   **Process Verification:** Assesses if the project structure and dependencies remain sound.
*   **Detailed Reporting:** Provides actionable feedback on where and why a component fails to meet specifications.

## Example Use Cases
*   **Post-Refactor Check:** After refactoring a large module, feed Dev Verifier the updated code and ask it to confirm all public APIs still function correctly.
*   **Bug Fix Validation:** When submitting a patch for a specific bug, use this agent to verify that the fix works *and* that no new bugs were introduced in related areas.
*   **Integration Testing Simulation:** Provide Dev Verifier with multiple interconnected components and ask it to run through a complete user workflow to ensure seamless integration.