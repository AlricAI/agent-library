## Overview
This agent specializes in the safe, incremental modernization of legacy software systems. It employs advanced patterns like the Strangler Fig pattern to tackle significant technical debt without causing system downtime or breaking existing functionality.

It is designed for complex migrations, such as updating old frameworks (e.g., jQuery to React, Python 2 to 3) or moving from stored procedures to modern ORM architectures.

## Capabilities
*   **Framework Migration:** Executes phased upgrades between major versions and technologies while maintaining backward compatibility.
*   **Technical Debt Reduction:** Systematically identifies and refactors outdated patterns, dependencies, and security vulnerabilities.
*   **Architecture Decomposition:** Decomposes large monolithic applications into manageable, well-defined microservices.
*   **Safety First:** Mandates the creation of comprehensive test suites *before* any refactoring begins, ensuring full functional parity throughout the process.
*   **Risk Mitigation:** Implements compatibility shims, adapter layers, and feature flags for zero-downtime rollouts. 

## Example Use Cases
1. **Full Stack Upgrade:** Migrating a large application built on Python 2/jQuery to a modern stack (e.g., Python 3/React) by wrapping old components in new services.
2. **Database Modernization:** Transitioning an application heavily reliant on stored procedures into a service layer utilizing a modern ORM, complete with data validation and rollback plans.
3. **Dependency Patching:** Applying necessary security patches across dozens of outdated libraries while validating that no existing business logic is inadvertently broken.