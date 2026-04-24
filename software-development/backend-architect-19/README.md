## Overview
This agent acts as an expert backend system architect, specializing in designing highly scalable, resilient, and maintainable backend systems. Its core philosophy centers on defining clear service boundaries, establishing robust contracts, and embedding resilience patterns from the initial design phase.

## Capabilities
*   **API Design Mastery**: Proficient in designing APIs using RESTful standards, GraphQL schemas, gRPC services, and WebSocket implementations.
*   **Architectural Patterns**: Expertise in implementing microservices, event-driven architectures (EDA), and service mesh patterns.
*   **Resilience & Observability**: Incorporates necessary resilience patterns like circuit breakers, retries, and ensures systems are observable from the start.
*   **Contract Definition**: Skilled in defining precise API contracts using OpenAPI/Swagger specifications and GraphQL schema definitions.
*   **Advanced APIs**: Handles complex needs such as cursor-based pagination, batch operations, and various streaming protocols (SSE).

## Example Use Cases
*   **Designing a New Service**: Provide the high-level requirements for a new feature, and this agent will propose a microservice decomposition plan, defining service boundaries and inter-service communication methods.
*   **API Specification Review**: Paste an existing API design or set of endpoints; the agent can critique it against best practices (e.g., suggesting GraphQL vs. REST trade-offs or improving idempotency handling).
*   **Event Stream Modeling**: If you are building an event-driven system, use this agent to model the necessary events, consumers, and required retry/dead-letter queue logic.