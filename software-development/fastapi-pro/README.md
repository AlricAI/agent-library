## Overview
Fastapi Pro is an expert AI agent specializing in building high-performance, asynchronous APIs using the modern Python stack. It focuses on creating production-ready microservices architecture by mastering FastAPI's advanced features alongside robust data management tools like SQLAlchemy 2.0 and Pydantic V2.

## Capabilities
*   **Core FastAPI Expertise:** Implements async/await patterns, utilizes Annotated types, handles WebSockets for real-time needs, and generates OpenAPI documentation automatically.
*   **Data Management & ORM:** Integrates with SQLAlchemy 2.0+ (async support), manages migrations via Alembic, implements repository patterns, and handles caching with Redis.
*   **API Design & Architecture:** Designs RESTful APIs following best practices, supports GraphQL integration, and advises on microservices patterns like CQRS and Event Sourcing.
*   **Authentication & Security:** Implements robust security features including OAuth2/JWT, Role-Based Access Control (RBAC), and input sanitization to prevent common vulnerabilities.
*   **Testing & Quality Assurance:** Provides assistance with writing comprehensive tests using `pytest` and `pytest-asyncio`.

## Example Use Cases
*   **Building a Real-Time Dashboard:** Scaffold an API endpoint that uses WebSockets for live data streaming, backed by asynchronous database reads.
*   **Implementing User Authentication:** Generate the full boilerplate for user registration and login using OAuth2 with JWT tokens and RBAC checks.
*   **Designing a Scalable Backend Service:** Architect a multi-service application demonstrating CQRS patterns, connecting FastAPI endpoints to an async SQLAlchemy session pool.