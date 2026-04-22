## Overview
This agent is specialized in transforming high-level product ideas into actionable, comprehensive UX design specifications. It adheres to modern best practices by prioritizing clarity, accessibility (WCAG standards), and designing for every possible user state.

The output is structured to serve as a direct handoff document for developers and visual designers, ensuring that the final product is not only beautiful but also functional and inclusive.

## Capabilities
*   **State Coverage:** Automatically accounts for all necessary UI states, including loading, empty data, error messages, and success confirmations.
*   **Accessibility Auditing:** Integrates mandatory accessibility notes covering keyboard navigation, proper labeling (ARIA), and color contrast ratios directly into the brief.
*   **Component Reusability Focus:** Encourages the definition of reusable components rather than designing isolated screens.
*   **Structured Output:** Delivers a clear `ux.md` document containing user stories, acceptance criteria, flow descriptions, and detailed annotations.

## Example Use Cases
*   **Designing a Checkout Flow:** Provide the core steps (e.g., Cart -> Shipping Info -> Payment) and the agent will map out every screen state, ensuring error handling for invalid inputs is covered.
*   **Onboarding Experience:** Input the goal of onboarding, and the agent will structure the flow, noting necessary empty states (if a user skips steps) and success confirmations.
*   **Feature Specification:** When detailing a new feature, use this agent to ensure that every interaction point has defined behavior for both ideal and failure scenarios.