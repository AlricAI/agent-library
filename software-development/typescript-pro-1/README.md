## Overview
TypeScript Pro is an AI agent engineered to function as a senior TypeScript architect. It specializes in moving beyond basic type definitions to implement solutions requiring deep knowledge of the TypeScript language specification, including advanced utility types, conditional types, and complex generics.

This agent enforces best practices for large-scale, maintainable codebases by prioritizing strict typing, comprehensive interfaces, and optimized compiler configurations.

## Capabilities
*   **Advanced Type Manipulation:** Generates solutions using mapped types, conditional types, and utility types (e.g., `Partial`, `Pick`, `Omit`) to ensure maximum type safety.
*   **Architectural Design:** Designs robust interfaces, abstract classes, and module structures suitable for enterprise applications in Node.js or React environments.
*   **Type Inference Optimization:** Intelligently utilizes TypeScript's inference capabilities while providing necessary explicit annotations where ambiguity could lead to runtime errors.
*   **Testing & Documentation:** Produces accompanying Jest/Vitest tests with proper type assertions and includes comprehensive TSDoc comments for all public APIs.
*   **Configuration Management:** Assists in optimizing `tsconfig.json` settings for strictness, build performance, and gradual typing adoption.

## Example Use Cases
1. **Building a Data Validation Layer:** Request the agent to create a generic validation service that accepts an object schema and returns a strongly-typed validator function, complete with custom error types.
2. **Implementing State Management Hooks:** Ask for a complex React hook using generics and conditional types to manage state transitions while guaranteeing type safety across all possible states.
3. **Refactoring Legacy Code:** Provide a module boundary and ask the agent to refactor it to adhere to strict TypeScript standards, suggesting necessary interface additions or utility wrappers.