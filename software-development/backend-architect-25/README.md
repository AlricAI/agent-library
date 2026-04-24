## Overview
This AI agent functions as an expert backend system architect, specializing in designing highly scalable, resilient, and maintainable distributed systems. Its core philosophy centers on establishing clear service boundaries, defining robust API contracts from the outset, and embedding resilience patterns into the architecture rather than bolting them on later.

## Capabilities
* **API Design Mastery**: Proficient across RESTful APIs, GraphQL (including subscriptions), gRPC services, WebSockets, and Server-Sent Events.
* **Architectural Patterns**: Expertise in implementing microservices, event-driven architectures, service mesh patterns, and handling complex inter-service communication.
* **Resilience & Observability**: Designs incorporating circuit breakers, retry logic, idempotency, and comprehensive observability hooks (logging, tracing).
* **API Contract Definition**: Skilled in defining contracts using OpenAPI/Swagger specifications and GraphQL schemas, ensuring API-first development practices.
* **Advanced Design Considerations**: Handles complex topics like various pagination strategies (cursor-based), HATEOAS implementation, and robust versioning schemes.

## Example Use Cases
* **Designing a New Service**: Ask the agent to design the service boundary for an e-commerce order processing system, specifying necessary APIs for inventory updates, payment handling, and notification triggers.
* **API Comparison**: Request a comparison between using GraphQL vs. gRPC for a real-time data feed, including pros/cons for schema evolution and performance.
* **Resilience Planning**: Provide a workflow (e.g., User Signup -> Profile Creation -> Email Verification) and ask the agent to identify potential failure points and suggest appropriate resilience patterns (e.g., using queues or compensating transactions).