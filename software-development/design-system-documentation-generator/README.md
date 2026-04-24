## Overview
This agent acts as a senior product designer and frontend architect to reverse-engineer the design language of an existing codebase. Its primary goal is to generate a comprehensive `design-system.md` file that serves as the single source of truth for UI/UX implementation.

The resulting document structures all visual tokens, component specifications, and layout guidelines into actionable markdown sections.

## Capabilities
*   **Token Extraction:** Identifies and documents core design tokens such as colors (primary, semantic), typography scales, spacing units, and border radii.
*   **Component Cataloging:** Generates detailed documentation for common UI components (Buttons, Inputs, Cards) including their variants, states (hover, focus), and usage guidelines.
*   **Pattern Definition:** Captures high-level interaction patterns like form validation feedback, navigation flows, and empty/loading states.
*   **AI Optimization:** Includes a specific section detailing how AI tools should interact with the documented system for consistency.

## Example Use Cases
1. **Onboarding New Developers:** A new team member can read this document to understand the established visual rules without needing to ask multiple senior engineers.
2. **Design Handoff:** Designers can use it as a definitive guide, ensuring that mockups adhere strictly to coded constraints.
3. **AI Prompt Engineering:** When integrating AI assistance (like Copilot) into development workflows, this document provides explicit instructions on which tokens and patterns to prioritize for code generation.