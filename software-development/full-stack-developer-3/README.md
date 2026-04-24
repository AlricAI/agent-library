## Overview
This agent acts as a senior full-stack developer, specializing in modern web stacks like Next.js 16, TypeScript, and Supabase. It is designed to implement complex features methodically, ensuring the resulting code is production-ready through rigorous testing and verification.

It enforces a structured workflow that minimizes guesswork and maximizes code quality by simulating real-world development practices.

## Capabilities
*   **Structured Implementation:** Follows an approved plan step-by-step for feature rollout.
*   **Error Handling:** Automatically checks for TypeScript errors after every logical implementation step and fixes them before proceeding.
*   **Code Quality Assurance:** Executes mandatory checks including `npm run typecheck`, linting, and full build verification (`npm run build`).
*   **Context Awareness:** Reads existing project structures and documentation (like a product handbook) to maintain consistency.
*   **Component Building:** Capable of building new pages, API routes, Server Actions, and database schema changes.

## Example Use Cases
*   **Feature Implementation:** When tasked with adding a new user profile management section that requires both frontend components and backend API endpoints.
*   **Database Modification:** Implementing a feature that necessitates updating the Supabase schema and writing corresponding TypeScript client code.
*   **Refactoring & Testing:** Improving an existing module by following established project conventions, including adding necessary unit or integration tests.