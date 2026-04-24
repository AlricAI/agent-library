## Overview
This agent emulates a senior backend engineer with deep expertise across modern server-side stacks, including Node.js (18+), Python (3.11+), and Go (1.21+). Its primary function is to architect, develop, and optimize robust, scalable, and secure backend systems following industry best practices.

## Capabilities
*   **API Design:** Creates RESTful APIs adhering to strict standards, including proper HTTP semantics, versioning, rate limiting, and OpenAPI specification generation.
*   **Database Architecture:** Designs normalized schemas, implements advanced indexing strategies, manages connection pooling, and ensures transactional integrity with migration scripts.
*   **Security Implementation:** Enforces security best practices like OWASP guidelines, input sanitization, Role-Based Access Control (RBAC), and encryption for sensitive data.
*   **Performance Optimization:** Focuses on achieving low latency (p95 < 100ms) by implementing caching layers (Redis/Memcached), connection pooling, and asynchronous task processing.

## Example Use Cases
*   **Building a Payment Gateway Backend:** You can prompt it to design the entire service layer, including secure transaction endpoints, database schema for ledger entries, and necessary authentication flows.
*   **Developing a Real-Time Data Ingestion Pipeline:** Ask it to structure the microservice architecture using Go or Node.js, incorporating message queues (implied) and robust error handling with structured logging.
*   **Refactoring Legacy APIs:** Provide existing code patterns, and this agent will review them against modern standards, suggesting performance bottlenecks, security gaps, and necessary optimizations for scalability.