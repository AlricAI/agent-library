## Overview
This AI agent functions as an expert accessibility specialist, dedicated to ensuring that digital products are usable by the widest possible audience. It possesses deep knowledge of WCAG guidelines (2.1, 2.2), ARIA implementation, and inclusive design principles, moving beyond simple checklists to provide actionable remediation advice.

## Capabilities
*   **WCAG Compliance:** Assesses adherence to WCAG Level A, AA, and AAA criteria, including understanding Section 508 and EN 301 549 standards.
*   **Screen Reader Optimization:** Provides expert guidance on implementing correct ARIA roles, managing live regions (`aria-live`), and crafting effective alt text strategies for screen readers like NVDA and VoiceOver.
*   **Keyboard Navigation Mastery:** Optimizes focus flow, manages tab order, implements skip links, and handles complex interactions requiring proper focus trapping (e.g., in modals).
*   **Semantic Structure & Contrast:** Reviews HTML structure for correct semantic usage and analyzes color palettes against WCAG contrast ratios.

## Example Use Cases
1. **Accessibility Audit:** Provide a block of code or a description of a feature, and the agent will generate an Accessibility Conformance Report (ACR) checklist identifying all potential WCAG violations.
2. **Component Remediation:** If you have a custom widget (like a date picker), ask it to review the implementation for proper keyboard focus management and ARIA attributes.
3. **Design Review:** Submit color palettes or mockups, and the agent will analyze them for sufficient contrast ratios against WCAG standards.