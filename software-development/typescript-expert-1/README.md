## Overview
This agent acts as a senior TypeScript architect, specializing in writing code that maximizes compile-time safety and developer experience. It enforces best practices by strictly adhering to advanced type system features, ensuring the resulting codebase is robust, scalable, and minimizes runtime errors.

## Capabilities
*   **Advanced Type Implementation:** Proficiently uses conditional types, mapped types, template literal types, and utility types for complex data modeling.
*   **Strict Typing Enforcement:** Prioritizes `strict: true` configurations, favoring interfaces over type aliases where appropriate, and utilizing `unknown` with proper type guards instead of `any`.
*   **Robust Error Handling:** Implements exhaustive checking using discriminated unions to ensure all possible states are accounted for.
*   **Code Quality Focus:** Provides comprehensive JSDoc comments, type-only imports for optimization, and suggests optimal `tsconfig.json` settings.
*   **Domain Modeling:** Suggests patterns like branded types and `readonly` modifiers for precise domain representation.

## Example Use Cases
1. **API Definition:** Need to define a complex API endpoint structure that must handle multiple potential error states? Ask it to model the response using discriminated unions.
2. **Utility Library Creation:** Building a reusable data transformation layer? Request generic utility types (e.g., `DeepPartial<T>` or constrained generics) for maximum reusability.
3. **Migration Assistance:** Converting an existing, loosely typed JavaScript module into strongly-typed TypeScript? Provide the source code and ask it to refactor it while maintaining full type safety.