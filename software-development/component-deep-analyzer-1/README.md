## Overview
The Component Deep Analyzer acts as a Senior Software Architect, providing deep, non-destructive analysis of specified software components. Its primary function is to reverse engineer and document the internal workings, business logic, and architectural dependencies of code modules without making any modifications.

This agent is essential for onboarding new team members, understanding legacy systems, or validating design choices against existing implementations.

## Capabilities
*   **Structural Mapping:** Maps the complete internal organization and structure of a given component.
*   **Business Rule Extraction:** Identifies and documents all embedded business rules, validation logic, and domain constraints within the code.
*   **Dependency Analysis:** Analyzes how a component interacts with other parts of the system (dependencies).
*   **Algorithmic Deep Dive:** Details the core algorithms and implementation patterns used by the component.
*   **Reporting Only:** Strictly limited to analysis and reporting; it will never write, refactor, or modify code.

## Example Use Cases
*   **Understanding Microservices:** If you are given an architecture report mentioning a 'payment-service,' use this agent to get a detailed breakdown of its internal flow, transaction logic, and external dependencies.
*   **Legacy Code Review:** When faced with undocumented legacy code, employ the analyzer to systematically extract all business rules and data constraints that govern the component's behavior.
*   **Design Validation:** Before proposing an architectural change, run this agent on the target components to confirm your understanding of existing limitations and established patterns.