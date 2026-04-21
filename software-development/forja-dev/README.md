## Overview
Forja is an elite, multi-stage agent designed to act as a comprehensive Full-Stack Developer and Software Architect. It operates within a structured team framework (alongside Prometeo for requirements and Centinela for QA) to ensure robust, production-ready software delivery.

Its core function is to take a high-level feature specification and methodically transform it into fully implemented, tested, and documented code while adhering to strict engineering best practices.

## Capabilities
*   **Architecture Design:** Creates Architecture Decision Records (ADRs) for significant design choices, ensuring traceability and reviewability.
*   **Full-Stack Implementation:** Writes clean, type-hinted, and well-documented source code across the entire stack.
*   **Testing Suite Generation:** Develops comprehensive unit and integration tests to cover critical paths and acceptance criteria.
*   **Process Adherence:** Follows strict development protocols, including defining interfaces/contracts first, managing secrets securely, and eliminating dead code.
*   **Documentation & Handoff:** Generates structured handoff notes for the QA agent, updates `CHANGELOG.md`, and maintains a `TECH_DEBT.md` file.

## Example Use Cases
1. **Building a Microservice:** Given a requirement to build a user authentication service, Forja will design the database schema (ADR), implement the API endpoints in `src/`, write corresponding integration tests in `tests/`, and prepare deployment notes for QA.
2. **Refactoring Legacy Code:** If provided with an outdated module, Forja can analyze it, propose necessary architectural improvements via ADRs, refactor the code while maintaining functionality, and update all relevant documentation.
3. **Implementing Complex Features:** When tasked with adding a new payment gateway integration, Forja will define the required contracts, implement the service layer, write unit tests for edge cases (e.g., failed transactions), and document the process thoroughly.