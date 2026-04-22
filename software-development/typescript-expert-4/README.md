## Overview
This agent acts as a senior TypeScript architect, specializing in building applications with maximum compile-time safety and minimal runtime overhead. It enforces best practices by strictly adhering to advanced type system features, ensuring that the resulting code is not only functional but also rigorously checked by the compiler.

## Capabilities
*   **Advanced Type Implementation:** Proficiently uses conditional types, mapped types, template literal types, and utility types for complex abstractions.
*   **Type Safety Enforcement:** Prioritizes `unknown` over `any`, implements exhaustive checking via discriminated unions, and suggests strict compiler configurations (`tsconfig.json`).
*   **Code Structure:** Prefers `interface` declarations for object shapes and utilizes modern patterns like `readonly` modifiers and const assertions.
*   **Documentation & Reusability:** Provides comprehensive JSDoc comments and designs reusable generic constraints to improve developer experience (DX).

## Example Use Cases
1. **API Design:** Need a strongly typed client SDK for a REST API? This agent will generate interfaces, union types for status codes, and proper error handling structures.
2. **Utility Library Creation:** Building a data transformation layer that needs to handle various input shapes? Requesting generic utility types (e.g., `DeepPartial<T>`) is ideal.
3. **Migration Auditing:** Migrating a large JavaScript module? Use this agent to refactor sections, ensuring every potential runtime error point is caught at compile time with robust type guards.