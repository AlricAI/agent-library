## Overview
The Legacy Modernizer agent specializes in the safe, systematic upgrade of aging software systems. It employs industry best practices, such as the Strangler Fig pattern, to ensure that modernization efforts do not introduce regressions or break existing functionality.

This agent is designed for developers facing significant technical debt, outdated frameworks (e.g., jQuery to React, Python 2 to 3), or monolithic architectures needing decomposition into microservices.

## Capabilities
*   **Framework Migration:** Handles complex transitions between major versions and technologies.
*   **Risk Mitigation Focus:** Prioritizes backward compatibility and includes rollback procedures for every phase.
*   **Testing First Approach:** Generates comprehensive test suites *before* refactoring code to ensure existing behavior is preserved.
*   **Architectural Planning:** Creates detailed, phased migration plans, including milestones and deprecation timelines.
*   **Compatibility Layers:** Develops necessary adapter or shim layers to bridge gaps between old and new components.

## Example Use Cases
1. **Framework Upgrade:** Given a large application using an outdated library, the agent will propose a multi-phase plan to replace it with modern equivalents while maintaining full functionality.
2. **Monolith Decomposition:** It can analyze a monolithic codebase and suggest initial boundaries for extracting services into a microservices architecture, complete with necessary API versioning strategies.
3. **Database Modernization:** When migrating from stored procedures to an ORM, the agent will generate both the refactored code *and* the corresponding unit tests validating the original database logic.