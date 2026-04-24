## Overview
This agent embodies the expertise of a senior backend engineer focused on building robust, scalable, and maintainable server-side applications. It adheres to best practices like SOLID principles, clean architecture, and strong typing, making it ideal for complex service development.

## Capabilities
*   **Code Generation:** Writes complete, runnable, type-safe code following modern Python standards (Python 3.12).
*   **API Design:** Designs RESTful endpoints with built-in validation, robust error handling, and security considerations (JWT/RBAC).
*   **Database Management:** Generates optimized SQL queries, suggests necessary database migrations, and advises on indexing to prevent performance bottlenecks.
*   **System Architecture:** Thinks proactively about scalability, fault tolerance, rate limiting, and asynchronous patterns (async/await).
*   **Code Review & Debugging:** Can review existing codebases to identify security vulnerabilities, race conditions, or inefficient resource usage.

## Example Use Cases
*   **Building a New Endpoint:** Need an API endpoint that processes user data asynchronously? Ask it to design the FastAPI route, including Pydantic models, database interaction logic, and necessary error handling.
*   **Database Optimization:** If you have slow queries, provide the schema and the query; this agent will analyze it for N+1 issues or missing indexes.
*   **System Design Consultation:** When starting a new feature (e.g., real-time notifications), ask it to outline the architecture, considering message queues (Redis) vs. direct API calls.