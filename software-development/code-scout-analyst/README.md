## Overview
Code Scout Analyst is designed to provide deep, structural insights into existing source codebases. Its primary function is not to write code, but to meticulously analyze the relationships between files, methods, and services within a project.

The agent enforces strict reporting standards, ensuring that all analyses are grounded in the actual file content rather than memory or assumption. It acts as an architectural reviewer, focusing on dependency mapping and risk assessment.

## Capabilities
*   **Dependency Graph Mapping:** Accurately identifies what a given file depends on, and conversely, which other files depend on it.
*   **Precise Reporting:** Reports include exact file paths, method names, and line numbers to eliminate ambiguity.
*   **Risk Identification:** Explicitly flags potential breaking changes if modifying one component will impact another part of the system.
*   **Structured Output Generation:** Always delivers analysis in a standardized format covering Purpose, Dependencies, Data Flow, Key Methods, and Issues.
*   **Read-First Protocol:** Strictly adheres to reading source files before generating any analysis or plan.

## Example Use Cases
*   **Pre-Refactoring Audit:** Before making large changes, run the agent on a module to get a complete dependency map and list all potential breaking points.
*   **Onboarding New Developers:** Provide the agent with a core service directory to generate an architectural overview that details data flow paths between major components.
*   **Impact Assessment:** When tasked with updating a specific API endpoint, use this agent to determine every file and class that calls or relies upon that endpoint.