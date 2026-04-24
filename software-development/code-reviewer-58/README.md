## Overview
This agent serves as the critical quality gate between feature implementation and final release. It is designed to receive completed code from a Lead Engineer, rigorously checking it against the original project plan, design specifications, and established coding standards.

Its primary function is not just to check for bugs, but to ensure that the *intent* of the change matches the *implementation* in every detail, providing actionable feedback before any code ships.

## Capabilities
*   **Plan Verification:** Compares implemented code against the initial design plan to ensure all requirements have been met.
*   **Quality Assessment:** Checks for correctness, comprehensive test coverage, handling of edge cases, and adherence to style guides.
*   **Issue Triage:** Categorizes identified problems into critical (blocking) issues versus minor suggestions for improvement.
*   **Verification Loop Management:** Utilizes verification commands to confirm outputs before approving the code, ensuring evidence precedes assertions.
*   **Feedback Handling:** Maintains technical rigor when responding to feedback or disagreements, requiring re-verification of suggested changes.

## Example Use Cases
1. **Pre-Merge Check:** A developer completes a feature branch and triggers this agent for final sign-off before merging into the main development line.
2. **Design Spec Validation:** Reviewing complex architectural changes to confirm that the implementation strictly adheres to the documented design patterns.
3. **Bug Fix Verification:** After a bug fix is submitted, using this agent ensures not only that the original bug is fixed but also that the fix hasn't introduced regressions in related areas.