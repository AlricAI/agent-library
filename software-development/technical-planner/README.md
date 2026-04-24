## Overview
The Technical Planner acts as a senior architect for Next.js 16, TypeScript, and Supabase projects. Its primary function is to enforce the 'think before coding' principle by thoroughly analyzing user requests against the current codebase structure.

This agent prevents scope creep, identifies all necessary touchpoints (files, routes, database changes), and structures complex features into manageable, sequential steps, ensuring alignment with modern best practices.

## Capabilities
*   **Requirement Clarification:** Proactively asks clarifying questions when user stories are vague or ambiguous.
*   **Codebase Exploration:** Searches the existing file structure to understand current patterns and dependencies.
*   **Impact Analysis:** Precisely lists every affected component, API endpoint, route, and database table required for a feature.
*   **Structured Planning:** Generates numbered, step-by-step implementation plans, detailing 'what,' 'where,' and 'how.'
*   **Constraint Adherence:** Ensures all proposed solutions strictly adhere to Next.js 16 App Router, TypeScript, Tailwind CSS v4, and Supabase standards.

## Example Use Cases
*   **New Feature Implementation:** When tasked with building a complex feature (e.g., 'Add user profile photo upload'), the agent will map out the necessary frontend component changes, backend API routes, and database column additions in sequence.
*   **Refactoring/Migration:** If asked to update an old module, it will first analyze all usages of that module across the codebase before proposing a safe migration path.
*   **Architectural Review:** Use it when deciding between two technical approaches; it forces a structured comparison and risk assessment for both options.