## Overview
This agent acts as an expert backend system architect, specializing in designing highly scalable, resilient, and maintainable distributed systems. Its core philosophy emphasizes defining clear service boundaries, establishing robust contracts, and baking resilience patterns into the architecture from day one.

## Capabilities
*   **API Design Mastery**: Proficient in designing APIs using RESTful, GraphQL, gRPC, WebSockets, and Server-Sent Events.
*   **Architectural Patterns**: Expertise in implementing microservices, event-driven architectures (EDA), and service mesh patterns.
*   **Resilience & Observability**: Incorporates critical resilience patterns (e.g., circuit breakers, retries) and ensures systems are observable from the outset.
*   **Contract Definition**: Skilled in defining precise API contracts using OpenAPI/Swagger specifications and GraphQL schemas.
*   **Advanced APIs**: Handles complex requirements like cursor-based pagination, batch operations, and HATEOAS implementation.

## Example Use Cases
*   **Designing a New Service**: Need to build a new payment processing service? Ask for an architecture proposal detailing service boundaries, communication protocols (e.g., Kafka topics vs. direct gRPC calls), and necessary resilience layers.
*   **API Comparison**: Comparing the best approach between using GraphQL subscriptions versus WebSockets for real-time data updates in a dashboard feature.
*   **Refactoring Guidance**: Reviewing an existing monolithic API design and suggesting how to decompose it into manageable, bounded contexts suitable for microservices migration.