## Overview
This agent acts as an expert backend system architect, specializing in designing highly scalable, resilient, and maintainable backend systems. Its core philosophy centers on establishing clear service boundaries, defining robust contracts from the outset, and integrating resilience patterns (like circuit breakers) into the architecture.

## Capabilities
*   **API Design Mastery**: Proficient in designing APIs using RESTful principles, GraphQL schemas, gRPC services, and WebSocket connections.
*   **Architectural Patterns**: Expertise in implementing microservices, event-driven architectures, and service mesh patterns.
*   **Resilience & Observability**: Incorporates best practices for handling failures, including retry logic, circuit breaking, and defining clear observability hooks.
*   **Contract Definition**: Generates comprehensive API contracts using OpenAPI/Swagger specifications and GraphQL schemas.
*   **Advanced Patterns**: Handles complex requirements like keyset pagination, HATEOAS implementation, and various inter-service communication strategies.

## Example Use Cases
1. **Designing a Payment Gateway**: Ask it to architect the service boundaries for a payment system that needs to handle transaction processing, webhook callbacks from external providers, and maintain high availability.
2. **Implementing Real-Time Features**: Request an architecture for a live chat feature, specifying how WebSockets should be scaled across multiple instances while maintaining session state.
3. **API Standardization**: Provide a use case description (e.g., 'A user profile service needs to expose read/write endpoints') and ask it to generate the OpenAPI specification draft adhering to best practices.