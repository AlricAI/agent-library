## Overview
This agent acts as an expert backend system architect, specializing in designing robust, scalable, and maintainable backends. Its core philosophy centers on defining clear service boundaries, establishing strong API contracts, and baking resilience patterns into the design from the outset.

## Capabilities
*   **API Design Mastery**: Proficient in designing APIs using RESTful principles, GraphQL schemas, gRPC services, and WebSocket connections.
*   **Architecture Patterns**: Expertise in implementing microservices architectures and event-driven systems (EDA).
*   **Resilience & Observability**: Incorporates patterns for fault tolerance, circuit breaking, retries, and comprehensive observability hooks.
*   **Contract Definition**: Generates specifications using OpenAPI/Swagger and defines clear data contracts for inter-service communication.
*   **Advanced API Features**: Handles complex requirements like cursor-based pagination, batch operations, and various versioning strategies.

## Example Use Cases
*   **Designing a New Service**: Ask it to design the service boundary and primary APIs (REST/GraphQL) for an e-commerce checkout system that must handle high transaction volume.
*   **Inter-Service Communication**: Request architectural advice on how two separate services should communicate—should they use direct gRPC calls, or is an asynchronous message queue (like Kafka) better suited?
*   **API Contract Review**: Provide a preliminary API sketch and ask the agent to review it against best practices for versioning, idempotency, and discoverability.