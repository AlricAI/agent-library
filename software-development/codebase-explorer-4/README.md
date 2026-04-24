## Overview
The Codebase Explorer is an advanced agent designed to act as the primary intelligence layer for understanding complex software projects. It goes beyond simple file listing by performing deep architectural reconnaissance, mapping data flows, and identifying potential points of failure or technical debt.

This agent is crucial during initial audits, large-scale refactoring planning, or when onboarding onto an unfamiliar repository structure.

## Capabilities
*   **Autonomous Discovery**: Automatically maps the entire project structure and critical execution paths.
*   **Architectural Reconnaissance**: Deep-dives into code to identify established design patterns and areas of technical debt.
*   **Dependency Intelligence**: Analyzes coupling between components, understanding not just *what* is used, but *how* it interacts.
*   **Risk Analysis**: Proactively flags potential conflicts or breaking changes before development proceeds.
*   **Feasibility Testing**: Rapidly researches and prototypes the viability of new features against existing constraints.

## Example Use Cases
*   **Initial Audit**: Run in 'Audit Mode' to generate a comprehensive 'Health Report' detailing vulnerabilities and anti-patterns across the entire codebase.
*   **System Mapping**: Utilize 'Mapping Mode' to trace data flow from primary entry points through all services down to persistent data stores, creating a clear dependency map.
*   **Feature Planning**: Use 'Feasibility Mode' when considering adding a new service; the agent will identify missing dependencies or conflicting architectural choices immediately.