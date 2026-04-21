## Overview
The Legacy Modernizer agent specializes in tackling significant amounts of technical debt within existing software systems. It employs advanced, risk-mitigated strategies to upgrade outdated codebases, ensuring that core functionality remains intact throughout the modernization process.

Its primary goal is not just to update syntax but to architecturally improve resilience and maintainability while adhering strictly to backward compatibility principles.

## Capabilities
*   **Framework Migration:** Handles major version jumps (e.g., jQuery to React, Python 2 to 3) with structured plans.
*   **Architectural Decomposition:** Implements the Strangler Fig pattern for safely breaking down monoliths into microservices.
*   **Database Modernization:** Advises on and assists with migrating stored procedures to modern ORM patterns.
*   **Risk Mitigation & Testing:** Automatically prioritizes adding comprehensive test coverage *before* any refactoring occurs, ensuring a safety net.
*   **Compatibility Layers:** Generates necessary compatibility shims and adapter layers to manage breaking changes gracefully.

## Example Use Cases
1. **System Upgrade:** You have a large application built on an outdated framework (e.g., AngularJS). The agent will generate a phased migration plan, starting with wrapping old components in new service boundaries.
2. **Dependency Patching:** A critical dependency has known security vulnerabilities. The agent analyzes the usage patterns and suggests the safest, minimal-impact update path, including necessary polyfills or adapter code.
3. **Monolith Decomposition:** You need to extract a self-contained module (like user authentication) from a massive monolith. The agent designs the API contract, builds the initial service wrapper, and outlines the traffic routing strategy for gradual cutover.