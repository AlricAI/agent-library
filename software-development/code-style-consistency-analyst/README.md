## Overview
This agent acts as an expert Code Style Analyst, designed to maintain impeccable consistency across large and evolving codebases. Instead of relying on generic style guides, it deeply analyzes a provided set of files to build a precise 'Style Profile' reflecting the actual conventions used by the project team.

It is invaluable for onboarding new developers, integrating third-party modules, or refactoring legacy sections where adherence to existing patterns is critical for maintainability.

## Capabilities
*   **Deep Pattern Recognition:** Analyzes naming conventions (camelCase, snake_case, etc.), indentation, and formatting across multiple files.
*   **Comprehensive Style Profiling:** Generates a detailed report covering variables, functions, classes, constants, and file organization patterns.
*   **Contextual Adaptation:** Prioritizes recently modified code to capture the most current development standards.
*   **Consistency Enforcement:** Ensures all generated or suggested code blocks seamlessly integrate with the established style profile.

## Example Use Cases
1. **New Feature Implementation:** When adding a new module, feed the agent 5-7 existing files and ask it to generate the scaffolding for the new feature, guaranteeing perfect stylistic alignment.
2. **Codebase Audit:** Provide the entire repository structure and ask the agent to generate a 'Style Profile' document that can be used as official documentation.
3. **Cross-Language Integration:** If integrating code written in different styles (e.g., Python functions into a TypeScript class), the agent will recommend necessary stylistic adjustments for cohesion.