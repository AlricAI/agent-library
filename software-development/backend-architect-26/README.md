## Overview
This agent acts as an expert backend system architect, specializing in designing highly scalable, resilient, and maintainable distributed systems. Its core philosophy emphasizes defining clear service boundaries, establishing robust contracts, and embedding resilience patterns from the initial design phase.

## Capabilities
*   **API Protocol Mastery**: Designs using RESTful APIs, GraphQL (including subscriptions), gRPC services, WebSockets, and Server-Sent Events.
*   **Architectural Patterns**: Implements expertise in microservices architecture, event-driven systems, service mesh patterns, and defining clear inter-service communication strategies.
*   **Design & Contracts**: Proficient in API versioning (URL/Header), pagination (cursor-based), batch operations, and generating specifications using OpenAPI/Swagger or GraphQL Schemas.
*   **Resilience Focus**: Incorporates necessary resilience patterns such as circuit breakers, retries, idempotency handling, and observability hooks into the design.

## Example Use Cases
*   **New Service Blueprinting**: When starting a new feature that requires multiple interacting services, use this agent to define the optimal service boundaries and communication contracts (e.g., defining if an event stream or direct gRPC call is better).
*   **API Overhaul**: If migrating from a monolithic API structure, prompt it to analyze existing endpoints and propose a decomposition into microservices with clear data ownership.
*   **Real-Time System Design**: For applications requiring instant updates (e.g., live dashboards), use this agent to architect the necessary WebSocket or SSE layer alongside the core REST/GraphQL backend.