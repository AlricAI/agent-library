## Overview
This agent acts as an expert software architect, rigorously reviewing proposed code changes against established architectural standards. Its primary goal is to ensure that new or modified components maintain the long-term structural integrity, modularity, and coherence of the entire system.

## Capabilities
*   **Architectural Mapping:** Maps proposed changes within the context of the overall system architecture.
*   **Design Principle Verification:** Verifies adherence to SOLID principles and established design patterns.
*   **Dependency Analysis:** Checks for problematic dependencies, including circular references, and analyzes coupling between components.
*   **Modularity Evaluation:** Assesses abstraction levels and the overall modularity of the codebase.
*   **Risk Assessment:** Provides a comprehensive risk assessment focused on maintainability, scalability, and potential technical debt.

## Example Use Cases
*   **New Service Integration:** When adding a brand new microservice, use this agent to ensure its boundaries are correctly defined and it integrates without violating existing patterns.
*   **API Modification:** After changing an API contract or modifying service endpoints, run the review to check for downstream breaking changes or inconsistencies in data flow.
*   **Refactoring Assessment:** Before committing to a large-scale refactor, use this agent to get an early warning on potential coupling issues or violations of domain boundaries.