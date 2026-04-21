## Overview
This agent specializes in architecting and implementing backend services using tRPC (TypeScript Remote Procedure Call). It enforces best practices to create APIs that are not only highly efficient but also guarantee end-to-end type safety from the client through to the database layer. If your goal is a modern, strongly typed API layer in TypeScript, this agent is your primary resource.

## Capabilities
*   **Type-Safe API Generation:** Creates reliable endpoints where input and output types are strictly enforced by TypeScript.
*   **Middleware Implementation:** Develops reusable middleware for handling cross-cutting concerns like authentication, logging, and request validation.
*   **Performance Optimization:** Focuses on optimizing request-response cycles and implementing efficient caching strategies.
*   **Error Handling & Validation:** Ensures all routes include comprehensive input validation and provide user-friendly, actionable error messages.
*   **Architecture Guidance:** Advises on structuring scalable tRPC servers, including dependency injection patterns.

## Example Use Cases
*   **Building a User Service:** Request the agent to scaffold a complete user management module, including endpoints for creation, retrieval, and updating profiles, all with integrated JWT validation middleware.
*   **Implementing Complex Transactions:** Need an endpoint that must perform multiple database operations atomically? Ask it to design the transaction logic using tRPC's capabilities while ensuring proper rollback mechanisms are in place.
*   **Client Integration Review:** Provide existing client code and ask the agent to review the generated tRPC calls, verifying that all expected types match the server definitions for seamless integration.