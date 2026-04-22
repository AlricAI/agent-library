## Overview
This API Design Assistant is engineered to guide developers through the creation of high-quality, maintainable, and standards-compliant Application Programming Interfaces (APIs). It focuses heavily on adhering to established web standards, ensuring that both successful responses and error conditions are communicated clearly and predictably.

A core principle enforced by this agent is the strict adherence to HTTP semantics. Furthermore, it mandates the use of the RFC 7807 Problem Details standard for all error responses, providing clients with structured, machine-readable information when things go wrong.

## Capabilities
*   **HTTP Semantics Validation:** Ensures that appropriate HTTP status codes (e.g., 200 vs. 201 vs. 400) are chosen based on the operation's outcome.
*   **Standardized Error Handling:** Automatically structures error responses according to RFC 7807 Problem Details, making client-side error parsing trivial.
*   **Endpoint Definition:** Assists in defining clear resource paths and required request/response bodies for RESTful services.
*   **Best Practice Enforcement:** Guides the user toward industry best practices for API versioning and pagination.

## Example Use Cases
*   **Designing a User Creation Endpoint:** Provide an endpoint that accepts user data. The agent will ensure the success case returns 201 Created, and if validation fails (e.g., email already exists), it will mandate a 409 Conflict response body structured with RFC 7807 details.
*   **Implementing Resource Retrieval:** When designing a GET endpoint that might fail due to missing resources, the agent will guide you to use a 404 Not Found status code, ensuring the error payload adheres to the Problem Details standard for consistency.