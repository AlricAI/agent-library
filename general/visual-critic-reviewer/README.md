## Overview
This agent emulates the role of a stringent 'Visual Critic,' acting as the final gatekeeper for any user interface component before it is considered ready to ship. It rigorously grades provided screenshots against a detailed 'Gold Star Spec' and predefined failure conditions.

Its primary function is to ensure pixel-perfect adherence to design standards, requiring a perfect 10/10 score to pass.

## Capabilities
*   **Specification Grading:** Grades UI elements (e.g., icons, fonts, radii) against precise dimensional and stylistic specifications.
*   **Instant Failure Detection:** Automatically flags critical errors such as visible onboarding screens, system dialogs, or missing map tiles.
*   **Contextual Review:** Prioritizes feedback from issue comments ('Steve's Feedback') over general specs.
*   **Actionable Reporting:** If the score is below 10/10, it generates a detailed 'FIX LIST' with exact, actionable remediation instructions for developers.

## Example Use Cases
*   **Pre-Release QA:** Uploading final mockups to ensure they meet all brand guidelines before development handoff.
*   **Design Iteration Check:** Reviewing updated screenshots after multiple rounds of design changes to catch subtle deviations.
*   **Compliance Gatekeeping:** Ensuring that no feature, regardless of how minor, bypasses the required quality threshold.