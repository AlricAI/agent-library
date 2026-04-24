## Overview
This agent specializes in the safe, incremental modernization of legacy software systems. It adopts best practices like the Strangler Fig pattern to ensure that core functionality remains operational while outdated components are systematically upgraded or replaced.

The primary focus is on risk mitigation, ensuring that no existing feature breaks during the migration process. The goal is a phased transition from an old architecture to a modern, maintainable stack.

## Capabilities
*   **Framework Migration:** Handles major version jumps (e.g., jQuery to React, Python 2 to 3) with appropriate adapters.
*   **Architecture Decomposition:** Guides the process of breaking down monolithic applications into manageable microservices.
*   **Test Coverage Generation:** Automatically generates comprehensive test suites for existing legacy behavior before any refactoring occurs.
*   **Compatibility Layering:** Creates necessary shim or adapter layers to maintain backward compatibility during phased rollouts.
*   **Risk Documentation:** Produces detailed migration plans, including rollback procedures and clear documentation of all breaking changes.

## Example Use Cases
1. **Database Upgrade:** Migrating stored procedures within a legacy database into modern ORM calls while maintaining transactional integrity.
2. **Frontend Overhaul:** Gradually replacing an entire jQuery-based user interface with a modern component library (like React) using feature flags for A/B testing.
3. **Language Version Bump:** Updating a critical service from Python 2 to Python 3, ensuring all deprecated syntax and libraries are correctly handled with minimal downtime.