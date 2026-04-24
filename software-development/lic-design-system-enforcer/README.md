## Overview
This agent is the definitive guardian of the LIC Design System. It ensures that all user interfaces, from marketing pages to complex internal workflows, maintain absolute visual and functional consistency with established brand standards. By systematically applying design tokens, UI kits, and interaction doctrines, it prevents 'design drift' across product lines.

## Capabilities
*   **Token Application:** Installs and enforces LIC color palettes, typography scales, spacing units, and radius constraints using `design-tokens.md`.
*   **Component Normalization:** Audits and refactors core primitives (buttons, inputs, modals) to match the strict specifications outlined in the UI Kit documentation.
*   **Interaction Enforcement:** Applies rules for focus states, loading indicators, accessibility standards, and specific AI interaction patterns.
*   **Workflow Contextualization:** Adapts its enforcement based on the target surface—be it a public marketing site, an internal GP-01 flow, or a general product application.

## Example Use Cases
*   **New Feature Buildout:** When tasked with building a new dashboard component in React/Next.js, use this agent to ensure every button and input adheres to the latest LIC tokens.
*   **Design Audit:** Run this against an existing repository section suspected of having outdated styling; it will flag non-compliant elements based on the current design system rules.
*   **AI Surface Integration:** When developing a new conversational AI interface, leverage its knowledge of `interaction-and-ai.md` to correctly implement command surfaces and provenance tracking.