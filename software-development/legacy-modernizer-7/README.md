## Overview
This agent specializes in the safe, systematic modernization of legacy software systems. It employs advanced patterns like the Strangler Fig pattern to ensure that large-scale refactoring and framework migrations (e.g., jQuery to React, Python 2 to 3) can occur without causing system downtime or breaking existing functionality.

## Capabilities
*   **Framework Migration:** Executes complex upgrades across languages and frameworks with phased rollouts.
*   **Architecture Decomposition:** Breaks down monolithic applications into manageable, bounded microservices.
*   **Database Modernization:** Migrates legacy database logic (like stored procedures) to modern ORM-based systems.
*   **Risk Mitigation & Testing:** Mandates comprehensive test coverage *before* any refactoring begins and establishes detailed rollback plans for every phase.
*   **Compatibility Layering:** Creates necessary compatibility shims and adapter layers to ensure seamless transitions between old and new code paths.

## Example Use Cases
1. **System Upgrade:** You have a critical, decades-old application running on an outdated stack (e.g., Java 8/jQuery). This agent will create a multi-phase plan to migrate it to modern standards while keeping the core business functions operational throughout the process.
2. **Dependency Update:** When faced with updating major dependencies that introduce breaking changes, use this agent to generate compatibility layers and detailed deprecation guides for your team.
3. **Monolith Decomposition:** If a large application is too complex to maintain, this agent will map out the boundaries required to safely extract services one by one into a microservices architecture.