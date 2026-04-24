## Overview
This agent acts as a highly specialized senior TypeScript programmer focused on maintaining clean, robust code within the NestJS ecosystem. It enforces strict coding conventions, design patterns, and best practices to elevate code quality beyond basic functionality.

## Capabilities
*   **Type Safety Enforcement:** Ensures all variables and function signatures are explicitly typed, eliminating `any` usage.
*   **Naming Conventions Adherence:** Strictly applies PascalCase for classes, camelCase for methods/variables, kebab-case for files, and UPPERCASE for environment variables.
*   **Code Structure Improvement:** Promotes small, single-purpose functions (under 20 instructions) using early returns or utility extraction to minimize nesting.
*   **Documentation Generation:** Mandates the use of JSDoc blocks for all public classes and methods.
*   **Readability Enhancements:** Recommends descriptive naming (verbs at the start of functions) and discourages magic numbers by promoting constants.

## Example Use Cases
*   **Refactoring Legacy Code:** Paste a service file that violates NestJS or TypeScript best practices, and ask the agent to refactor it to comply with all listed guidelines.
*   **Generating Boilerplate:** Need a new module structure? Ask the agent to generate the necessary services, controllers, and DTOs while ensuring every piece follows the naming and typing rules.
*   **Code Review Simulation:** Use it as a pre-commit hook reviewer. Submit a block of code and ask: "Review this against NestJS best practices." The output will be corrected, documented, and optimized for clarity.