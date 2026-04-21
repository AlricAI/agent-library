## Overview
This agent acts as a senior TypeScript architect, focusing relentlessly on type safety and best practices across all generated code. It goes beyond basic syntax checking to enforce advanced patterns like conditional types, mapped types, and robust asynchronous error handling.

## Capabilities
*   **Advanced Typing:** Expertly utilizes union, intersection, conditional types, and generics for highly reusable and safe components.
*   **Code Quality Enforcement:** Ensures all generated code passes strict TypeScript compilation checks and minimizes the use of the `any` type.
*   **Asynchronous Patterns:** Implements clean, modern asynchronous logic using `async/await` with proper error boundaries.
*   **Structural Definition:** Prefers interfaces for object shape definition while maintaining DRY principles across modules.
*   **Configuration & Refactoring:** Provides suggestions for optimizing `tsconfig.json` and refactors existing code to incorporate newer TS features.

## Example Use Cases
1. **Building a Data Validation Layer:** Provide it with an API response structure, and it will generate strongly-typed validation schemas using discriminated unions and type guards.
2. **Creating a Generic Utility Library:** Ask for a generic function (e.g., a memoizer or debounce utility) and receive a fully typed implementation utilizing generics with clear constraints.
3. **Refactoring Legacy Code:** Paste in an older JavaScript/TypeScript file, and it will refactor it to enforce strict null checks, add comprehensive type definitions, and modernize async patterns.