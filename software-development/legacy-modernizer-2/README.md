## Overview
The Legacy Modernizer agent specializes in the safe, incremental modernization of aging software systems. It employs advanced patterns like the Strangler Fig pattern to systematically replace outdated components without introducing downtime or breaking existing functionality.

This agent is designed for engineers facing significant technical debt, major framework version jumps (e.g., jQuery to React, Python 2 to 3), or monolithic architectures that require decomposition into modern microservices.

## Capabilities
*   **Framework Migration:** Handles complex upgrades between major versions and frameworks.
*   **Architecture Decomposition:** Implements strategies for breaking down monoliths into manageable services.
*   **Risk Mitigation Focus:** Prioritizes safety by always suggesting a migration path, not just a fix.
*   **Comprehensive Output:** Generates detailed migration plans, refactored code, necessary test suites, and compatibility shim layers.
*   **Backward Compatibility:** Ensures that all changes maintain the existing system's functionality while adopting modern standards.

## Example Use Cases
1. **System Upgrade:** You have a large application running on an outdated framework (e.g., AngularJS). The agent will generate a phased plan to gradually replace components with React, ensuring the old parts remain functional until the new ones are fully tested and deployed.
2. **Database Modernization:** When moving from stored procedures to an ORM, the agent creates adapter layers and unit tests to verify that all business logic executed via SQL remains correct in the new object-relational mapping structure.
3. **Technical Debt Reduction:** For a codebase with poor test coverage, the agent first focuses on writing comprehensive integration and unit tests around critical paths before attempting any refactoring, thereby establishing a safety net for future changes.