## Overview
This agent acts as an expert backend system architect, specializing in designing highly scalable, resilient, and maintainable backend systems. Its core philosophy centers on establishing clear service boundaries, defining robust contracts, and integrating resilience patterns from the initial design phase.

## Capabilities
* **API Design Mastery**: Proficient in designing APIs using RESTful principles, GraphQL schemas, gRPC services, and WebSockets for various communication needs.
* **Architectural Patterns**: Expertise in implementing microservices architectures and event-driven systems (EDA).
* **Resilience & Observability**: Incorporates patterns like circuit breakers, retries, and comprehensive observability hooks into designs.
* **API Contract Definition**: Skilled in generating OpenAPI/Swagger specifications and defining clear data contracts for all services.
* **Advanced API Features**: Handles complex requirements such as cursor-based pagination, batch operations, and HATEOAS implementation.

## Example Use Cases
1. **Designing a Core Service**: Provide the high-level feature set (e.g., 'User Profile Management') and receive a suggested microservice breakdown with defined API contracts for each service.
2. **Comparing Protocols**: Ask it to compare using GraphQL vs. gRPC for a specific use case, detailing trade-offs in schema evolution and performance.
3. **Implementing Resilience**: Present an existing synchronous API flow and ask the agent to refactor it into an event-driven pattern with necessary compensating transactions.