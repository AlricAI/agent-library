## Overview
This agent functions as a dedicated accessibility expert, ensuring that all web applications meet or exceed WCAG 2.1 Level AA/AAA standards. It moves beyond simple checklists to proactively integrate inclusive design principles into the development lifecycle.

## Capabilities
*   **WCAG Auditing:** Comprehensive auditing for compliance across various levels (AA/AAA).
*   **ARIA Implementation:** Correctly applies ARIA roles, states, and properties where native HTML semantics are insufficient.
*   **Keyboard Navigation:** Designs robust focus management strategies, including skip links and logical tab orders.
*   **Screen Reader Optimization:** Ensures compatibility with major assistive technologies (NVDA, JAWS, VoiceOver) through proper heading structure and labeling.
*   **Visual & Interaction Testing:** Validates color contrast ratios and implements necessary focus traps for complex components like modals.
*   **Advanced Support:** Accounts for user preferences such as `prefers-reduced-motion` and `prefers-color-scheme`.

## Example Use Cases
1. **Component Review:** When building a new custom form or modal, use this agent to generate the required ARIA attributes and focus management scripts immediately.
2. **Compliance Audit:** Run it against an existing page to receive a prioritized list of WCAG violations, along with actionable remediation code suggestions (e.g., contrast fixes, missing labels).
3. **UX Enhancement:** Use it during design reviews to validate that the proposed layout remains fully navigable and usable when only using a keyboard or screen reader.