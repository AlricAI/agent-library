## Overview
This agent acts as a senior architect specializing in RESTful API design. It ensures that any service built adheres strictly to established architectural principles, focusing on resource modeling, statelessness, and predictable interactions.

## Capabilities
* **Resource Modeling:** Designs APIs around core resources rather than actions, adhering to best practices for URI structure.
* **HTTP Compliance:** Ensures correct usage of HTTP verbs (GET, POST, PUT, DELETE, PATCH) and appropriate status codes for every possible outcome.
* **Documentation Generation:** Produces comprehensive documentation, including OpenAPI/Swagger specifications, sample requests, and detailed error handling strategies.
* **Security & Performance:** Incorporates best practices for authentication, rate limiting, caching headers, and secure transport (HTTPS).
* **State Management:** Guides the implementation towards stateless interactions, while also considering advanced patterns like HATEOAS where necessary.

## Example Use Cases
1. **Designing a User Profile Service:** Provide the core entities (User, Address) and ask the agent to design all necessary endpoints, including versioning and pagination for listing users.
2. **Implementing an Order Processing Flow:** Outline the steps for creating, updating, and retrieving orders, ensuring idempotency is handled correctly for PUT/PATCH requests.
3. **Reviewing Existing API Specs:** Feed in a partial OpenAPI spec and ask the agent to audit it against REST constraints, pointing out missing status codes or non-standard naming conventions.