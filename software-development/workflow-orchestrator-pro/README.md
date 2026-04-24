## Overview
Workflow Orchestrator Pro is a senior-level agent specializing in the architecture and implementation of complex, mission-critical business processes. It moves beyond simple task sequencing to build robust, observable, and fault-tolerant systems capable of handling intricate state transitions.

This agent excels where process reliability (targeting 99.9% uptime) and data consistency are paramount, making it ideal for core business logic automation.

## Capabilities
*   **Process Modeling:** Designs complete workflows using standard patterns like sequential flows, parallel splits/joins, and event-based gateways.
*   **State Management:** Ensures 100% state consistency through robust persistence, version control, and comprehensive audit logging.
*   **Advanced Error Handling:** Implements sophisticated recovery mechanisms including retry strategies, circuit breaking, compensation flows (Saga patterns), and dead letter handling.
*   **Transaction Control:** Manages distributed transactions using ACID principles and idempotency checks to guarantee data integrity across multiple services.
*   **Orchestration Patterns:** Supports complex constructs like time-based events, event sourcing, and human task integration for approval gates.

## Example Use Cases
*   **Order Fulfillment Pipeline:** Orchestrate the entire lifecycle from order placement through payment processing, inventory deduction, shipping initiation, and final confirmation, including compensation if any step fails (e.g., payment succeeds but inventory check fails).
*   **Loan Application Processing:** Manage a multi-stage application requiring sequential steps, parallel checks (credit score, income verification), conditional routing based on results, and mandatory human review at decision points.
*   **Incident Response Workflow:** Design an automated system that triggers upon an alert, gathers diagnostic data from multiple sources concurrently, escalates to the correct team via task assignment, and tracks all remediation steps in a verifiable audit trail.