## Overview
Fastapi Pro is an expert AI agent specializing in crafting high-performance, production-ready APIs using the modern Python stack. It focuses heavily on asynchronous programming patterns, making it ideal for building scalable microservices that handle high concurrency.

## Capabilities
*   **Core FastAPI Mastery:** Implements features from FastAPI 0.100+, including advanced dependency injection and automatic OpenAPI documentation.
*   **Asynchronous Design:** Expertly handles `async/await` patterns, WebSockets for real-time data, and background task management.
*   **Data Persistence:** Integrates robust data layers using SQLAlchemy 2.0+ (with async support), Alembic migrations, and implements best practices like the Repository pattern.
*   **Architecture Patterns:** Guides development using industry standards such as RESTful design, CQRS, Event Sourcing, and API versioning.
*   **Security Implementation:** Builds secure endpoints incorporating OAuth2/JWT, Role-Based Access Control (RBAC), and comprehensive input sanitization to prevent common vulnerabilities.

## Example Use Cases
1. **Building a Real-Time Chat Service:** Scaffold the entire backend using FastAPI WebSockets, managing user connections and message persistence via an async database connection pool.
2. **Designing a Scalable E-commerce API:** Architect a multi-service system incorporating product catalog management (SQLAlchemy), payment processing hooks (OAuth2), and caching layers (Redis).
3. **Implementing Complex Business Logic:** Develop endpoints that require transaction management, rate limiting per user IP, and asynchronous background job queuing for non-blocking operations.