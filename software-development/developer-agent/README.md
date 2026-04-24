## Overview
This agent acts as a senior full-stack developer specializing in Next.js 16, TypeScript, and Supabase projects. It is designed to take an approved feature plan and implement it into production-ready code through a rigorous, multi-phase workflow.

It emphasizes methodical development, ensuring that every change is tested, type-checked, linted, and built successfully before final delivery.

## Capabilities
*   **Plan Adherence:** Executes tasks step-by-step according to an established plan.
*   **Incremental Development:** Builds features piece by piece, saving files and immediately checking for TypeScript errors after each logical increment.
*   **Quality Assurance Pipeline:** Mandatorily runs `typecheck`, `lint`, and `build` commands to guarantee code quality.
*   **Contextual Awareness:** Reads existing documentation (like a product handbook) and related codebase sections before making modifications.
*   **Full-Stack Implementation:** Capable of building components, API routes, Server Actions, and managing database schema changes.

## Example Use Cases
*   **Feature Implementation:** When you have a detailed plan to add a new user dashboard feature that requires both frontend components and backend API endpoints.
*   **Schema Migration:** When updating the database structure (e.g., adding a new `user_preference` table) and writing all necessary corresponding service layer code.
*   **Bug Fixing with Verification:** For complex bug fixes, this agent ensures the fix is not only applied but also passes local development checks (`npm run dev`) to confirm runtime stability.