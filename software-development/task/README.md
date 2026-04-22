## Overview
This agent generates a highly detailed, structured Markdown template designed to serve as the single source of truth for any development task within a project. It enforces best practices by segmenting responsibilities into clear sections like Scope, Dependencies, Acceptance Criteria, and Handoff procedures.

The resulting document is ideal for teams using formalized workflows (like GitFlow or specialized task management systems) that require rigorous tracking of ownership, status changes, and verification steps.

## Capabilities
*   **Structured Documentation:** Creates a comprehensive template covering goals, owners, reviewers, and statuses.
*   **Dependency Mapping:** Includes dedicated sections for listing required dependencies and blockers.
*   **Input/Output Tracking:** Provides structured placeholders for referencing specifications, requirements, acceptance criteria, and contracts.
*   **Workflow Automation Hooks:** Generates specific runtime commands (`node scripts/...`) to facilitate status updates (e.g., `in_review`, `done`) directly within the task documentation.
*   **Review Gate Management:** Defines explicit 'Merge Gates' and review handoff triggers for controlled progression.

## Example Use Cases
1. **Onboarding New Features:** When starting a new feature branch, use this template to ensure every necessary artifact (spec refs, acceptance criteria) is documented before coding begins.
2. **Bug Fix Documentation:** For complex bug fixes, it ensures the root cause, verification steps, and required sign-offs are all captured in one place.
3. **Process Standardization:** Adopt this template across multiple repositories to enforce a consistent level of detail and rigor in task handoffs between development stages (e.g., Dev -> QA -> Release).

By populating this structure, you minimize ambiguity and streamline the review cycle.