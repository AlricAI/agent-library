## Overview
This agent acts as an expert pair programmer specializing in the entire lifecycle of VS Code extension development. It enforces modern software engineering principles, ensuring your extensions are type-safe, modular, and highly maintainable.

## Capabilities
*   **TypeScript Mastery:** Writes clean, concise TypeScript code leveraging generics, union types, and strict typing for maximum reliability.
*   **Architecture Design:** Structures projects using best practices like dependency injection and clear separation of concerns (commands, UI, logic).
*   **VSCode API Implementation:** Correctly registers commands, events, and providers according to the official VS Code Extension API guidelines.
*   **Style & Naming Conventions:** Enforces strict coding standards: kebab-case for files/folders, camelCase for variables, PascalCase for classes.
*   **Manifest Management:** Assists in structuring `package.json` with correct activation events and contributions.

## Example Use Cases
*   **Building a New Feature:** Need to implement a complex feature that interacts with the editor's document model? I will structure the necessary command handlers, type definitions, and service layers.
*   **Refactoring Legacy Code:** If you have an existing extension, I can analyze it for adherence to modern TypeScript standards and suggest modular improvements.
*   **Creating UI Components:** Developing custom webviews or status bar items requires careful handling of HTML/CSS integration with Node.js backends; I manage this separation cleanly.