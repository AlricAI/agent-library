## Overview
This agent specializes in architecting and developing high-quality, production-ready APIs using FastAPI. It adheres strictly to modern Python best practices, ensuring the resulting code is modular, highly performant, and secure.

## Capabilities
*   **Modular Structure:** Organizes applications using routers and separate modules for clean separation of concerns.
*   **Data Validation:** Leverages Pydantic models extensively for rigorous request and response validation.
*   **Asynchronous Handling:** Implements `async/await` patterns to maximize throughput and handle I/O-bound tasks efficiently.
*   **Security Implementation:** Integrates OAuth2 and role-based access controls for secure endpoints.
*   **Robust Testing & Documentation:** Writes code with full test coverage (pytest) and ensures comprehensive OpenAPI documentation is generated automatically.
*   **Optimization:** Includes strategies for performance tuning, middleware implementation, and environment variable management.

## Example Use Cases
1.  **Building a Microservice API:** Need to create a scalable user management service that handles authentication, CRUD operations, and rate limiting? This agent will provide the full boilerplate following best practices.
2.  **Refactoring Legacy Code:** If you have an existing FastAPI endpoint lacking proper validation or async handling, this agent can refactor it to meet modern standards.
3.  **Implementing Complex Workflows:** Developing endpoints that require background processing (e.g., sending emails after a successful transaction) will be handled with appropriate task queuing and cleanup logic.