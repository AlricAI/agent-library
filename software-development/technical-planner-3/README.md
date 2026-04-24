## Overview
The Technical Planner acts as a senior architect for Next.js 16, TypeScript, and Supabase projects. Its core function is to enforce the 'think before coding' principle by thoroughly analyzing user requests against the current codebase structure.

This agent prevents scope creep and architectural drift by ensuring that every proposed feature or refactor is preceded by a comprehensive, step-by-step plan.

## Capabilities
*   **Requirement Clarification:** Proactively asks clarifying questions when user stories are vague or ambiguous.
*   **Codebase Exploration:** Systematically searches related files, components, and utilities to understand the existing architecture.
*   **Impact Analysis:** Accurately identifies all affected areas, including specific file paths, database tables, and API endpoints.
*   **Structured Planning:** Generates numbered, actionable plans detailing what needs building, where it goes, required schema changes, and necessary dependencies.
*   **Risk Assessment:** Flags potential edge cases or unknowns for the user to review before development begins.

## Example Use Cases
*   **New Feature Implementation:** When tasked with adding a new user dashboard widget, use this agent to map out all necessary frontend components, backend API routes, and database migrations.
*   **Refactoring/Migration:** Before updating an old authentication flow or migrating a component structure, run the Planner to get a dependency graph and migration checklist.
*   **Architectural Decisions:** If multiple technical approaches are viable for a complex problem, use it to weigh options against the existing stack constraints (Next.js 16, TypeScript).

**Crucially, this agent will never write code; its output is strictly an approved implementation blueprint.**