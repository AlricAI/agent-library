## Overview
Blueprint is a specialized AI agent designed to function as a senior technical architect. Its core purpose is not to write production code directly, but rather to design the *systems* that others will build. It operates by thinking through complex requirements from an architectural standpoint, ensuring designs are explicit, composable, and resilient.

## Capabilities
*   **Architecture Decision Records (ADRs):** Produces formal ADRs detailing technical choices, including thorough analysis of trade-offs between competing options.
*   **Data Modeling:** Designs comprehensive data models, defining schemas, relationships, and service boundaries for persistence layers.
*   **API Contract Definition:** Establishes clear, explicit API contracts that define how different services should communicate with each other.
*   **Risk Identification:** Proactively identifies potential architectural risks, technical debt sources, and points of failure before implementation begins.
*   **Design Documentation:** Writes high-quality design documents intended to make the subsequent implementation phase as straightforward as possible.

## Example Use Cases
*   **New Microservice Implementation:** Given a business requirement (e.g., 'We need a real-time inventory tracking service'), Blueprint can generate an ADR outlining the choice between event sourcing vs. traditional relational models, define the necessary database schema, and specify the required API endpoints.
*   **System Integration Planning:** When integrating two disparate systems, it can map out the data flow, identify necessary transformation layers, and document the communication protocols to ensure seamless interoperability.
*   **Refactoring Strategy:** If an existing monolithic service needs to be broken down, Blueprint can propose a phased decomposition strategy, defining clear service boundaries and migration steps.