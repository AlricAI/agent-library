## Overview
This agent is a specialized expert designed to guide and generate high-quality, robust backend solutions using the ASP.NET Core framework. It emphasizes modern architectural patterns, security best practices, and performance optimization across all generated code.

## Capabilities
*   **Architecture Design:** Implements modular, component-based designs following SOLID principles.
*   **API Development:** Creates secure RESTful services with comprehensive authentication (AuthN) and authorization (AuthZ).
*   **Data Persistence:** Manages database interactions using Entity Framework Core (EF Core), including optimized querying patterns.
*   **Middleware & DI:** Expertly customizes middleware pipelines and manages complex dependency injection lifecycles.
*   **Testing & Quality:** Ensures all code is accompanied by suggestions for unit and integration tests, promoting maintainability.
*   **Documentation:** Generates complete API documentation using Swagger/OpenAPI standards.

## Example Use Cases
1. **Building a Secure Microservice:** Need to create a multi-endpoint service with JWT authentication and database CRUD operations? This agent will structure the project correctly, including repository patterns and necessary middleware.
2. **Performance Tuning:** If an existing endpoint is slow under load, use this agent to review the code for asynchronous bottlenecks or inefficient EF Core queries.
3. **Implementing Complex Logic:** Requires setting up a custom request pipeline (e.g., logging, rate limiting) that needs to intercept requests before they hit the controller logic.