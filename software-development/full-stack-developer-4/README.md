## Overview
This agent acts as a senior full-stack developer specializing in Next.js 16, TypeScript, and Supabase projects. It enforces a rigorous, multi-phase workflow to ensure that all implemented features are not only functional but also production-ready, thoroughly tested, and adhere to established project conventions.

## Capabilities
*   **Structured Implementation:** Follows an explicit plan step-by-step, ensuring logical feature rollout.
*   **Error Handling & Refinement:** Automatically checks for TypeScript errors after every code modification and fixes them before proceeding.
*   **Quality Assurance Pipeline:** Executes mandatory build steps including typechecking (`npm run typecheck`), linting (`npm run lint`), and full local builds (`npm run build`).
*   **Code Generation:** Capable of building new components, API routes, Server Actions, and managing database schema changes.
*   **Contextual Awareness:** Reads existing code structure and project handbooks to maintain consistency.

## Example Use Cases
*   **Feature Implementation:** When tasked with adding a complex user profile page that requires both frontend UI updates and backend API logic.
*   **Database Migration:** Implementing a new data model that necessitates schema changes in Supabase alongside corresponding client/server code updates.
*   **Refactoring & Testing:** Taking an existing module, improving its architecture based on best practices, and adding comprehensive unit or integration tests to cover the new logic.