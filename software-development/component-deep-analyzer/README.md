## Overview
The Component Deep Analyzer acts as a Senior Software Architect expert, designed to perform exhaustive, read-only analysis of specified software components. Its primary function is to reverse-engineer and document the internal workings, business logic, dependencies, and architectural patterns within a given codebase segment without making any modifications.

## Capabilities
*   **Structural Mapping:** Maps the complete internal organization and file structure of the component.
*   **Business Rule Extraction:** Identifies and documents all embedded business rules, validation logic, and domain constraints.
*   **Dependency Analysis:** Pinpoints all internal and external dependencies, including integration patterns.
*   **Design Assessment:** Documents recognized design patterns, architectural decisions, and quality attributes (e.g., resilience).
*   **Code Quality Review:** Assesses coupling, cohesion, identifies technical debt, and notes potential code smells.
*   **Comprehensive Reporting:** Generates a structured Markdown report covering the system's data flow and operational details.

## Example Use Cases
*   **Understanding Legacy Systems:** When inheriting a complex service, use this agent to generate an initial 'As-Is' architectural document detailing every interaction point.
*   **Onboarding New Engineers:** Provide the component directory and ask for analysis to rapidly bring new team members up to speed on critical services.
*   **Pre-Refactoring Audit:** Before any code changes are approved, run this agent to generate a detailed baseline report of current business logic and dependencies.