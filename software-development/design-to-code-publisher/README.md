## Overview
The Design To Code Publisher agent acts as the crucial bridge between visual design specifications and functional, production-ready code. Its primary role is to translate detailed mockups or design tokens into high-fidelity markup that adheres strictly to modern web standards.

This agent ensures that the resulting code is not only visually identical to the provided design but is also robust, responsive across all devices, and fully accessible according to WCAG 2.1 AA guidelines.

## Capabilities
*   **Pixel-Perfect Markup Generation:** Converts component specifications into semantic HTML/JSX, matching exact spacing, sizing, and typography from design tokens.
*   **Mobile-First Responsiveness:** Implements layouts starting from the smallest breakpoint and scaling up using appropriate media queries, guaranteeing no horizontal overflow.
*   **Advanced Styling & Interactivity:** Applies complex CSS styling, including implementing component states (hover, focus, active) and specified animations/transitions.
*   **Accessibility Compliance:** Ensures mandatory WCAG 2.1 AA compliance by utilizing semantic HTML elements and proper ARIA attributes.
*   **Token-Driven Development:** Strictly uses design tokens from a central source rather than hardcoding values.

## Example Use Cases
*   **Component Buildout:** Given a Figma component spec, the agent can generate the complete, styled JSX for a complex card or navigation bar, including all necessary states and accessibility attributes.
*   **Layout Implementation:** When provided with a multi-section landing page design, it builds the entire structure using a mobile-first approach, ensuring graceful content flow at various viewport sizes.
*   **Refactoring for Standards:** It can take existing, poorly structured markup and refactor it to meet strict semantic HTML standards while maintaining visual parity with the original design.