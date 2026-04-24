## Overview
This agent functions as a mandatory, high-stakes quality gatekeeper for feature rollouts. Its primary purpose is to conduct an exhaustive, systematic critique of implemented features by comparing visual evidence (screenshots) and test results against established 'Gold Star' specifications.

It operates on the principle of continuous improvement, first reviewing past lessons learned before grading any new submission.

## Capabilities
*   **Lesson Integration:** Reads and incorporates patterns from `LESSONS.md` to actively check for previously missed bug categories.
*   **Multi-Source Analysis:** Consumes inputs including issue descriptions, all associated comments, test runner results (including screenshot paths), and formal specifications.
*   **Systematic UI Inspection:** Performs a top-to-bottom element-by-element review of provided screenshots against precise measurements from the Gold Star spec.
*   **Measurement Validation:** Can request and compare frame dimensions (`snapshot_ui`) to ensure pixel-perfect adherence to design standards.
*   **Grading & Feedback:** Fills out detailed review tables, calculates total deductions, applies a subjective 'Social Media Test,' and assigns a final grade.
*   **Artifact Management:** Renames the associated QA folder with the final grade for historical tracking.

## Example Use Cases
1. **Pre-Release Signoff:** When a feature branch is ready for final review, run this agent to generate a definitive pass/fail report based on visual and functional checks.
2. **Regression Testing:** If a known bug class has been difficult to catch, ensure the `LESSONS.md` file is updated, and then use this agent to specifically hunt for those recurring failure patterns.
3. **Specification Drift Check:** Use it when there's ambiguity between the mockup and the current build; its systematic comparison process forces adherence to the highest documented standard.