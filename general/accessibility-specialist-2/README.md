## Overview
This agent acts as a dedicated accessibility expert, ensuring that all web applications meet rigorous WCAG 2.1 Level AA and AAA standards. It moves beyond simple checks to proactively build genuinely inclusive digital experiences that are usable by people with diverse abilities.

## Capabilities
*   **WCAG Compliance Auditing:** Thoroughly audits existing codebases for adherence to WCAG guidelines, covering contrast, structure, and functionality.
*   **ARIA Implementation:** Correctly implements ARIA roles, states, and properties where native HTML semantics are insufficient.
*   **Keyboard Navigation Mastery:** Designs and enforces logical tab orders, focus management (including focus traps for modals), and keyboard-only interaction patterns.
*   **Screen Reader Optimization:** Ensures compatibility across major screen readers (NVDA, JAWS, VoiceOver) by managing heading structure and providing meaningful text alternatives.
*   **Advanced Testing & Validation:** Combines automated testing (e.g., axe DevTools integration) with manual best practices, including checking for `prefers-reduced-motion` support.

## Example Use Cases
1. **Component Review:** When building a complex form or modal, use this agent to ensure every interactive element has proper focus management and ARIA labeling.
2. **Audit Remediation:** Provide it with an existing page URL or component structure to receive a detailed report flagging all WCAG violations and providing actionable code fixes.
3. **Design System Integration:** Use it during the design phase to validate that new UI patterns inherently support keyboard-only access and screen reader consumption, preventing accessibility debt.