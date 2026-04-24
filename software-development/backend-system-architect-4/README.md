## Overview
Backend System Architect is a comprehensive AI specialist designed to handle the entire lifecycle of building robust, scalable server-side applications. It possesses deep expertise across modern architectural patterns, including microservices, event-driven systems, and advanced API design (REST, GraphQL, gRPC).

This agent excels at taking high-level requirements and translating them into detailed, actionable technical blueprints, complete with technology stack recommendations, data models, and implementation guidance.

## Capabilities
* **API Design:** Generates OpenAPI/Swagger specs, designs complex GraphQL schemas, and implements versioning strategies for both REST and GraphQL endpoints.
* **Microservices Architecture:** Decomposes monolithic systems into bounded contexts, advises on inter-service communication (Kafka, RabbitMQ), and applies resilience patterns like Circuit Breakers.
* **Technology Stack Mastery:** Provides expert code guidance in TypeScript/Node.js using frameworks like NestJS or Fastify, ensuring adherence to modern typing standards.
* **Data Persistence:** Manages complex database interactions across SQL (PostgreSQL) and NoSQL (MongoDB, Redis), focusing on transaction integrity, connection pooling, and query optimization.
* **Security Implementation:** Implements industry-standard authentication flows including JWT management, OAuth 2.0, and Role-Based Access Control (RBAC).

## Example Use Cases
* **Designing a Payment Gateway:** Ask it to design the microservice boundaries for a payment system, specifying Kafka topics for transaction events, defining the required GraphQL mutation for processing payments, and outlining the necessary RBAC roles.
* **Optimizing Database Queries:** Provide an existing ORM query that is slow, and ask the agent to refactor it, suggesting appropriate caching layers (Redis) and identifying potential N+1 issues.
* **Building a User Service API:** Request a complete boilerplate structure for a user service using NestJS and TypeScript, including JWT generation middleware, rate limiting logic, and proper OpenAPI documentation scaffolding.