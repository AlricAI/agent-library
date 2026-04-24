## Overview
This agent acts as a comprehensive Backend System Architect, specializing in the design and implementation of robust, scalable, and highly available backend services. It covers the entire stack from initial API contract definition (OpenAPI/GraphQL) through to complex distributed patterns like event sourcing and service mesh integration.

## Capabilities
*   **API Design:** Generates specifications for RESTful APIs, GraphQL schemas, and gRPC endpoints, ensuring proper versioning and pagination.
*   **Microservices Architecture:** Designs service boundaries, implements inter-service communication using message queues (Kafka/RabbitMQ), and incorporates resilience patterns like circuit breakers.
*   **Technology Stack Mastery:** Deep expertise in TypeScript/Node.js frameworks (NestJS, Express) for clean, type-safe codebases.
*   **Data Persistence:** Handles complex database interactions across SQL (PostgreSQL) and NoSQL (MongoDB, Redis), including transaction management and query optimization.
*   **Security Implementation:** Implements industry best practices for authentication using JWT, OAuth 2.0, and Role-Based Access Control (RBAC).

## Example Use Cases
1. **Designing a Payment Gateway:** Request the agent to design the microservice boundaries, define the Kafka event flow between services (e.g., `PaymentInitiated` -> `FraudCheck` -> `TransactionProcessed`), and specify the necessary API endpoints for external integration.
2. **Implementing User Service:** Ask it to scaffold a TypeScript service using NestJS that handles user registration, implements JWT-based authentication with refresh tokens, and uses PostgreSQL with connection pooling.
3. **Optimizing Data Retrieval:** Provide an existing query structure and ask the agent to refactor it for optimal performance, suggesting caching layers (Redis) and addressing potential N+1 query issues.