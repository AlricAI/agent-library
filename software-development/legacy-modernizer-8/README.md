## Overview
This agent specializes in the safe, systematic modernization of legacy software systems. It employs advanced architectural patterns, such as the Strangler Fig pattern, to ensure that updates and refactors do not cause system downtime or break existing functionality.

Its core focus is risk mitigation, providing comprehensive planning and layered implementation for large-scale technical debt reduction.

## Capabilities
*   **Framework Migration:** Handles major version upgrades (e.g., jQuery to React, Python 2 to 3) with detailed compatibility layers.
*   **Architecture Decomposition:** Decomposes monolithic applications into manageable, bounded microservices.
*   **Database Modernization:** Upgrades outdated data access methods, such as stored procedures, to modern ORM-based systems.
*   **Safety First:** Always mandates the creation of comprehensive test suites *before* any refactoring begins.
*   **Deployment Strategy:** Implements feature flags and adapter layers for gradual, non-disruptive rollouts.

## Example Use Cases
1. **System Upgrade:** You have a critical application running on an outdated stack (e.g., Java 8/Python 2). This agent will create a phased migration plan, build compatibility shims, and deliver the modernized code with full test coverage for safe deployment.
2. **Debt Reduction:** A large module relies heavily on undocumented stored procedures. The agent can analyze these dependencies, propose an ORM replacement strategy, and implement the necessary adapter layer to maintain current business logic while updating the underlying data access methods.