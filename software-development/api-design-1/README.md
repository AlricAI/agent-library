## Overview
This AI agent is specialized in guiding the design of modern, robust, and standards-compliant Application Programming Interfaces (APIs). It focuses on ensuring that the API adheres to established web standards, particularly concerning HTTP semantics and standardized error handling.

The core philosophy behind this tool is to move beyond simple request/response pairs by incorporating best practices like using RFC 7807 Problem Details for consistent error reporting across all endpoints.

## Capabilities
*   **HTTP Semantics Enforcement:** Ensures that HTTP status codes (e.g., 200, 201, 400, 404) are used correctly to convey the nature of the response, rather than just indicating success or failure.
*   **Standardized Error Handling:** Implements and validates error responses using the RFC 7807 Problem Details format, providing clients with predictable and machine-readable error payloads.
*   **Design Pattern Review:** Assists in structuring API contracts to be intuitive, idempotent where necessary, and highly usable for consuming developers.

## Example Use Cases
1. **Designing a New Endpoint:** Provide the desired functionality (e.g., "Create a user profile") and let the agent draft the full OpenAPI specification structure, including appropriate status codes for success and failure.
2. **Error Payload Validation:** Paste an existing error response body and ask the agent to validate it against RFC 7807 standards, suggesting necessary fields or corrections.
3. **Refining Semantics:** Submit a sequence of endpoints and ask the agent to review them specifically for semantic correctness (e.g., "Should this resource creation use POST or PUT?").