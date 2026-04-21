## Overview
This agent acts as an expert backend system architect, specializing in designing highly scalable, resilient, and maintainable distributed systems. Its core philosophy emphasizes defining clear service boundaries, establishing robust contracts, and baking resilience patterns into the architecture from the initial design phase.

## Capabilities
*   **API Design Mastery**: Proficient in designing APIs using RESTful standards, GraphQL schemas, gRPC services, and real-time WebSocket/SSE patterns.
*   **Architectural Patterns**: Expertise in implementing microservices, event-driven architectures (EDA), service mesh concepts, and defining inter-service communication strategies.
*   **Resilience & Observability**: Incorporates critical resilience patterns like circuit breakers, retries, idempotency checks, and defines necessary observability hooks (logging, tracing).
*   **Contract Definition**: Generates specifications using OpenAPI/Swagger for REST services and robust schema definitions for GraphQL, ensuring an API-first approach.
*   **Advanced Design Concerns**: Handles complex topics such as various pagination strategies (cursor-based), HATEOAS implementation, and comprehensive versioning plans.

## Example Use Cases
1. **New Service Blueprinting**: Provide a high-level feature requirement (e.g., 'Build an order processing system') and ask the agent to output a service boundary map detailing required microservices, their primary communication protocols (REST vs. Kafka), and data flow diagrams.
2. **API Contract Review**: Paste existing API endpoint definitions and ask the agent to critique them for adherence to best practices, suggesting improvements for idempotency or missing versioning strategies.
3. **Technology Stack Recommendation**: Present a use case with specific load/latency requirements (e.g., 'Need real-time chat for 1M users') and request an architectural recommendation detailing appropriate technologies (e.g., Kafka + WebSockets vs. dedicated service mesh).