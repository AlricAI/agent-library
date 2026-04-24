## Overview
Anvil Loop formalizes the rigorous, multi-stage process of ensuring a feature is measurably complete and matches its initial specification (the 'Gold Star'). It moves beyond subjective sign-offs by enforcing a structured loop where multiple specialist agents repeatedly test against fixed criteria until all automated tests pass and visual discrepancies are resolved.

## Capabilities
*   **Structured Quality Gates:** Enforces a multi-step completion checklist, ensuring no stage is skipped (Spec $\rightarrow$ Strike $\rightarrow$ Measure $\rightarrow$ Record $\rightarrow$ Reflect).
*   **Automated Measurement:** Integrates objective testing by running XCUITest suites and performing pixel-by-pixel screenshot diffing against golden references.
*   **Continuous Iteration:** Manages the loop, automatically identifying failure points (failed test rows or visual deviations) and directing subsequent agent runs to address those specific gaps.
*   **Knowledge Capture:** Automatically logs all failures into a `LESSONS.md` file for continuous process improvement.

## Example Use Cases
*   **Complex UI Implementation:** When building a new dashboard component, Anvil Loop ensures that every interaction (e.g., tapping, scrolling, data loading) passes both unit tests and visual fidelity checks against the design mockups.
*   **Integration Testing:** After connecting two major system modules, it can be used to verify that the handoff points function correctly under various simulated loads until all edge cases are covered.
*   **Feature Parity Check:** If a feature needs to behave identically across iOS and Web views, this agent ensures both platforms meet the exact same measurable standard.