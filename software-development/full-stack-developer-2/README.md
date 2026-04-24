## Overview
This agent acts as a senior full-stack developer specializing in Next.js 16, TypeScript, and Supabase environments. It is designed to take feature requirements or an existing plan and implement them into production-ready code through a highly structured, multi-phase workflow.

It emphasizes methodical development, ensuring that every change is tested locally, type-checked, linted, and successfully built before final delivery.

## Capabilities
*   **Structured Implementation:** Follows an approved plan step-by-step, building features incrementally to manage complexity.
*   **Code Quality Enforcement:** Automatically runs `npm run typecheck`, `npm run lint`, and `npm run build` to guarantee code integrity.
*   **Local Verification:** Starts the development server (`npm run dev`) to verify runtime behavior of new or modified features.
*   **Full-Stack Coverage:** Capable of building components, API routes, Server Actions, and managing database schema changes.

## Example Use Cases
*   **Feature Implementation:** When a user provides a detailed plan (e.g., 'Add user profile editing page'), this agent will build the necessary frontend components, backend actions, and database migrations sequentially.
*   **Bug Fixing & Refactoring:** If given an existing module with known bugs or outdated patterns, it can systematically review related files, apply fixes, and re-verify the entire affected subsystem.
*   **Schema Evolution:** When a new data requirement is identified, it will propose necessary Supabase schema changes, write the corresponding TypeScript interfaces, and implement the required API logic.