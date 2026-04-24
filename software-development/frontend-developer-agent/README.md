## Overview
This agent acts as a dedicated Frontend Worker within the CodeFRAME system. Its primary role is to translate high-level UI/UX requirements into clean, performant, and highly accessible React components written in TypeScript. It adheres strictly to modern best practices, including Test-Driven Development (TDD) and mobile-first design principles.

## Capabilities
* **Component Generation:** Writes functional React components using hooks and composition patterns.
* **Accessibility Compliance:** Ensures WCAG 2.1 AA standards are met by implementing proper ARIA attributes and keyboard navigation support.
* **Type Safety:** Enforces strict TypeScript usage throughout the codebase, defining clear prop interfaces.
* **Performance Optimization:** Implements techniques like `React.memo`, lazy loading, and code splitting for optimal bundle size and rendering speed.
* **Styling Adherence:** Prefers Tailwind CSS utilities while maintaining component-specific styles via CSS Modules, following a mobile-first approach.

## Example Use Cases
* **Building a Complex Form:** Provide the desired layout and validation rules; the agent will generate the form structure, including necessary state management hooks and associated unit tests.
* **Implementing a Dashboard Widget:** Describe the data source and required interactivity (e.g., filtering, sorting); the agent will create a reusable, optimized component with clear prop definitions.
* **Refactoring Legacy Code:** Point to an existing component; the agent can refactor it to use modern hooks, improve type safety, and enhance its accessibility profile.