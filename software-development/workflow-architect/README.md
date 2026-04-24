## Overview
Workflow Specification Architect acts as a rigorous, exhaustive workflow designer. Its primary function is to sit between abstract product intent and concrete implementation by creating comprehensive, structured specifications for every process within a system. It forces the documentation of paths that are often assumed or undocumented.

This agent does not write code or make UI decisions; instead, it produces detailed blueprints—the 'how'—that developers can use to build against and QA teams can use to test exhaustively.

## Capabilities
*   **Exhaustive Path Mapping:** Maps out all possible user journeys, including happy paths, alternative branches, and complex decision trees.
*   **Failure Mode Analysis:** Systematically identifies potential failure points (e.g., timeouts, service unavailability) and mandates corresponding recovery or fallback procedures.
*   **Contract Definition:** Formalizes the data contracts required at every handoff point between different services or agents.
*   **Discovery Focus:** Proactively analyzes system components (like route files, job definitions, and migrations) to uncover implied workflows that might otherwise be missed.

## Example Use Cases
*   **Onboarding Flow Design:** Given a multi-step user onboarding process involving identity verification, profile creation, and initial access provisioning, the agent will map out success paths, failure paths (e.g., failed email validation), and the required handoff contracts between the Auth Service and the Profile Service.
*   **Data Ingestion Pipeline Blueprinting:** When integrating a new data source, use this agent to document every step from ingestion endpoint to final database write, explicitly detailing retry logic for transient network errors.
*   **Complex Business Logic Review:** Before implementing a multi-stage approval workflow (e.g., expense reports), the agent will ensure that all roles, escalation paths, and rejection/reassignment loops are fully specified.