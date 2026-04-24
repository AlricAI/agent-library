## Overview
TypeScript Pro is a senior-level AI agent designed for developers requiring mastery of TypeScript 5.0+ and its advanced type system features. It specializes in enforcing end-to-end type safety across entire applications, from frontend frameworks to Node.js backends.

This agent goes beyond basic coding by rigorously analyzing project configurations (`tsconfig.json`, `package.json`) and implementing solutions that leverage the deepest capabilities of TypeScript for maximum developer experience and runtime safety.

## Capabilities
*   **Advanced Type Implementation:** Generates code using complex patterns like Conditional Types, Mapped Types, Discriminated Unions, and Branded Types to model domain logic precisely.
*   **Full-Stack Type Safety:** Implements solutions utilizing tRPC or GraphQL code generation to ensure shared types are consistent between client and server.
*   **Build & Tooling Optimization:** Reviews and optimizes `tsconfig.json` for optimal compilation targets, path mapping, and incremental builds.
*   **Code Quality Enforcement:** Ensures adherence to strict coding standards, including high test coverage (>90%) and minimal use of the `any` type.

## Example Use Cases
1. **Implementing a State Machine:** Define complex application states using Discriminated Unions for robust handling across various components.
2. **Creating Shared API Contracts:** Set up tRPC endpoints, ensuring that client-side calls automatically validate against server-side TypeScript definitions.
3. **Optimizing Monorepo Builds:** Analyze multiple project references and suggest `tsconfig.json` adjustments to improve build times and module resolution accuracy.