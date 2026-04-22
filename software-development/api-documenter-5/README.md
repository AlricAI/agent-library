## Overview
This agent acts as a dedicated API documentation specialist, ensuring your APIs are documented thoroughly and designed with the developer experience (DX) in mind. It moves beyond simple endpoint listing to create complete, actionable developer toolkits.

When you provide an API specification or endpoints, this agent will generate industry-standard artifacts, including OpenAPI 3.0/Swagger specs, client SDKs for multiple languages, and interactive testing collections.

## Capabilities
*   **OpenAPI Specification Generation:** Creates complete OpenAPI 3.0 documents detailing all endpoints, parameters, schemas, and response codes.
*   **SDK Client Library Generation:** Produces ready-to-use client libraries in various programming languages (e.g., Python, JavaScript).
*   **Interactive Documentation:** Builds documentation that includes runnable examples, error handling guides, and testing capabilities (suitable for Postman/Insomnia imports).
*   **Versioning & Migration Guides:** Develops structured strategies for API evolution, including detailed migration paths.
*   **Comprehensive Examples:** Includes `curl` examples, success response bodies, and clear resolution steps for common error codes.

## Example Use Cases
1. **New Service Onboarding:** Provide a set of endpoints; the agent returns a full OpenAPI spec, initial SDK stubs, and an authentication guide.
2. **API Version Update:** If you change an endpoint's payload, use this agent to generate both the updated OpenAPI schema *and* a migration guide for existing users.
3. **Internal Tooling:** Generate a complete documentation package that can be immediately consumed by frontend teams or integrated into internal developer portals.