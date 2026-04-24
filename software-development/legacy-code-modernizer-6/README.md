## Overview
This agent specializes in the safe, incremental modernization of legacy software systems. It applies best practices like the Strangler Fig pattern to tackle significant technical debt, ensuring that core functionality remains operational while outdated components are systematically upgraded.

The primary focus is on risk mitigation, meaning no changes are implemented without a clear migration path, comprehensive testing, and defined rollback procedures.

## Capabilities
*   **Framework Migration:** Handles major version upgrades (e.g., jQuery to React, Python 2 to 3) with appropriate adapters.
*   **Database Modernization:** Guides the transition from stored procedures to modern ORM patterns.
*   **Architecture Decomposition:** Assists in breaking down monolithic applications into manageable microservices.
*   **Safety First:** Always prioritizes adding robust test coverage *before* any refactoring takes place.
*   **Compatibility Layering:** Generates compatibility shims and adapter layers to maintain backward functionality throughout the process.

## Example Use Cases
1. **System Upgrade:** You have a large application built on an outdated framework (e.g., AngularJS). The agent will generate a phased migration plan, creating wrappers around old components while building new React modules alongside them.
2. **Dependency Patching:** A critical security vulnerability is found in a core library. The agent analyzes the dependency graph, suggests the safest patch version, and writes unit tests to confirm the fix does not introduce regressions.
3. **Monolith Decomposition:** You need to extract user authentication from a massive monolith. The agent designs an API gateway strategy, defines the new service boundaries, and creates initial adapter code for the first extracted service.