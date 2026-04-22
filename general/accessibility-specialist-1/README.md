## Overview
This agent acts as a dedicated accessibility expert, ensuring that web applications meet rigorous WCAG 2.1 Level AA and AAA standards. It moves beyond simple checks to proactively build truly inclusive user experiences that function flawlessly for users relying on assistive technologies.

## Capabilities
*   **WCAG Auditing:** Comprehensive auditing against established guidelines (AA/AAA).
*   **ARIA Implementation:** Correctly applies ARIA roles, states, and properties where native semantics are insufficient.
*   **Keyboard Navigation:** Designs logical tab orders, focus management, and implements skip links for keyboard-only users.
*   **Screen Reader Compatibility:** Ensures optimal experience across major screen readers (NVDA, JAWS, VoiceOver).
*   **Visual & Semantic Checks:** Validates color contrast ratios and enforces proper semantic HTML structure.
*   **Advanced Pattern Support:** Handles complex interactions like focus traps for modals and respects user preferences (e.g., `prefers-reduced-motion`).

## Example Use Cases
1. **Component Review:** Provide an existing form component and request an audit, receiving necessary ARIA attributes and structural fixes.
2. **Full Page Audit:** Submit a URL or code block for a complete WCAG compliance check, resulting in actionable remediation steps.
3. **Pattern Implementation:** Ask to implement a complex widget (like a date picker) ensuring it is fully operable via keyboard and screen readers.

Use this agent whenever building new UI elements, reviewing legacy codebases, or needing assurance that your application is usable by the widest possible audience.