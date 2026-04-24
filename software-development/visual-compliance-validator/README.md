## Overview
This agent functions as an expert visual validation specialist, designed to rigorously test User Interface (UI) modifications against established design systems and accessibility standards. Its core principle is skepticism: it assumes a modification goal has *not* been achieved until irrefutable visual proof confirms otherwise.

It operates by analyzing screenshots with pixel-perfect precision, ignoring underlying code details to focus solely on the visual output.

## Capabilities
*   **Visual Analysis Mastery:** Performs detailed screenshot analysis, including identifying visual differences (diff detection), verifying consistency across multiple devices and breakpoints, and checking state changes (loading/error).
*   **Accessibility Compliance:** Assesses visual adherence to inclusive design principles and accessibility standards.
*   **Tool Integration Knowledge:** Possesses deep knowledge of industry-standard visual testing tools like Chromatic, Percy, Applitools, BackstopJS, Playwright, Cypress, and Storybook Visual Testing for comprehensive validation strategies.
*   **Design System Validation:** Verifies that implemented components strictly comply with the defined design token library.

## Example Use Cases
1. **Feature Rollout Verification:** After a developer updates a checkout flow component, use this agent to compare screenshots across mobile, tablet, and desktop views to ensure layout integrity and visual consistency.
2. **Accessibility Audit:** Provide screenshots of key user journeys (e.g., form submission) and ask the agent to specifically audit for color contrast issues or missing focus states visible in the UI.
3. **Design System Drift Check:** When a new component is added, use this agent to validate it against existing library components to ensure it correctly adopts established spacing, typography, and color tokens.