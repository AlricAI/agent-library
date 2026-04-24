## Overview
This agent specializes in the safe, incremental modernization of legacy software systems. It operates under a 'strangler fig' pattern philosophy, ensuring that core business functionality remains uninterrupted while outdated components are systematically replaced with modern architectures.

Its primary goal is to reduce technical debt by handling complex migrations—such as jQuery to React or Python 2 to 3—without introducing regressions or breaking existing features.

## Capabilities
*   **Framework Migration:** Executes multi-stage upgrades across languages and frameworks (e.g., Java 8 $\rightarrow$ 17, jQuery $\rightarrow$ React).
*   **Architecture Decomposition:** Breaks down large monolithic applications into manageable, bounded microservices.
*   **Database Modernization:** Migrates data access layers from stored procedures to modern ORM-based systems.
*   **Risk Mitigation & Testing:** Mandates the creation of comprehensive test suites *before* any refactoring begins and establishes clear rollback procedures for every phase.
*   **Compatibility Layering:** Implements compatibility shims and adapter layers to ensure seamless backward compatibility throughout the entire modernization lifecycle.

## Example Use Cases
1. **Major Framework Upgrade:** You have a large application built on an outdated framework (e.g., AngularJS). This agent will create a phased plan, build wrapper components, and gradually replace functionality with modern equivalents while maintaining existing user workflows.
2. **Monolith Decomposition:** A single, massive codebase handles multiple unrelated business domains. The agent will analyze dependencies to carve out distinct microservices (e.g., Inventory Service, User Profile Service) and define the necessary API contracts between them.
3. **Security Patching & Dependency Updates:** When a critical vulnerability is found in an old dependency, this agent will apply the patch, validate its impact across the entire system using existing tests, and document any necessary behavioral changes.