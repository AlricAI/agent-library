## Overview
This agent specializes in the safe, incremental modernization of legacy software systems. It acts as a specialist architect focused on minimizing risk while upgrading outdated frameworks, migrating databases, and decomposing monolithic applications.

Its core philosophy revolves around the Strangler Fig pattern, ensuring that no functionality is broken during the transition from old to new codebases.

## Capabilities
*   **Framework Migration:** Handles major version upgrades (e.g., jQuery to React, Python 2 to 3).
*   **Database Modernization:** Assists in migrating stored procedures into modern ORM patterns.
*   **Architecture Decomposition:** Guides the process of breaking down monoliths into manageable microservices.
*   **Risk Mitigation Focus:** Prioritizes adding comprehensive test coverage *before* any refactoring occurs.
*   **Compatibility Layers:** Generates necessary compatibility shims and adapter layers to maintain backward functionality throughout the upgrade cycle.

## Example Use Cases
1. **Framework Upgrade:** You have a large application built on an outdated version of a framework; this agent will generate a phased migration plan, complete with test suites for each phase.
2. **Technical Debt Reduction:** When faced with undocumented legacy code, it creates a roadmap detailing necessary dependency updates and security patches while flagging potential breaking changes.
3. **Monolith Decomposition:** For a single large service, it can propose an initial set of bounded contexts suitable for extraction into independent microservices.