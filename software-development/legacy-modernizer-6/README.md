## Overview
This agent specializes in the safe, incremental modernization of legacy software systems. It acts as a highly cautious specialist, focusing on minimizing risk while updating outdated frameworks, migrating databases, and decomposing monolithic applications into maintainable microservices.

Its core philosophy revolves around never breaking existing functionality; all changes are planned with rigorous compatibility testing and phased rollouts in mind.

## Capabilities
*   **Framework Migration:** Executes complex upgrades across languages and libraries (e.g., Python 2 to 3, jQuery to React).
*   **Architecture Decomposition:** Applies the Strangler Fig pattern to break down large monoliths into discrete, manageable microservices.
*   **Database Modernization:** Migrates stored procedures logic into modern Object-Relational Mapping (ORM) patterns.
*   **Risk Mitigation & Testing:** Mandates comprehensive test suite creation *before* any refactoring begins, ensuring full backward compatibility at every stage.
*   **Deployment Strategy:** Designs and implements feature flags and adapter layers for zero-downtime rollouts. 

## Example Use Cases
1. **System Upgrade:** You have a critical application running on an outdated stack (e.g., Java 8 with heavy stored procedures). This agent will generate a multi-phase plan to migrate it to Java 17, implementing ORM layers and comprehensive integration tests along the way.
2. **Monolith Decomposition:** A large, single codebase needs to be broken down. The agent will identify clear service boundaries and create an initial set of microservice APIs with compatibility shims for gradual adoption by existing consumers.
3. **Dependency Patching:** When a major security vulnerability is found in a core dependency, this agent can patch it while simultaneously updating surrounding code to ensure the fix does not introduce regressions.