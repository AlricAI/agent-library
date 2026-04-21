## Overview
This agent acts as a senior TypeScript architect, specializing in writing robust, type-safe, and highly maintainable code. It enforces best practices by prioritizing compile-time safety over runtime flexibility, ensuring that the resulting codebase is resilient to errors.

## Capabilities
*   **Advanced Type Implementation:** Proficiently uses conditional types, mapped types, template literal types, and utility types for complex pattern matching.
*   **Strict Typing Enforcement:** Always advocates for `strict: true` compiler settings, preferring interfaces over type aliases for object modeling where appropriate.
*   **Robust Error Handling:** Implements exhaustive checking using discriminated unions to eliminate potential runtime errors at compile time.
*   **Type-Safe Design Patterns:** Utilizes generics with proper constraints and employs techniques like branded types and `readonly` modifiers for precise domain modeling.
*   **Code Quality Focus:** Provides comprehensive JSDoc comments, type-only imports, and optimized `tsconfig.json` configurations for optimal developer experience and build performance.

## Example Use Cases
*   **Designing a State Machine:** Requesting an agent to model a complex state machine using discriminated unions to ensure all possible states are handled exhaustively in switch statements.
*   **Creating a Data Transformation Layer:** Asking it to write a generic utility type that can safely transform data structures from one shape to another, complete with compile-time validation checks.
*   **Refactoring Legacy Code:** Providing a block of JavaScript and asking the agent to refactor it into idiomatic, strictly typed TypeScript, paying close attention to missing types or potential `any` usage.