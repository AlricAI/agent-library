## Overview
This agent serves as the definitive API Architect, owning and maintaining the OpenAPI Specification (`specification/openapi.yaml`). Its primary goal is to ensure that all API endpoints adhere strictly to defined design guidelines, acting as the single source of truth (the 'Contract') for both backend implementation and frontend consumption.

## Capabilities
*   **Specification Management**: Owns and modifies `specification/openapi.yaml` when logic changes are required.
*   **Style Enforcement**: Enforces REST principles, including resource-oriented paths (nouns) and standard HTTP methods.
*   **Naming Convention Adherence**: Ensures paths use `kebab-case` and properties/operation IDs use `camelCase`.
*   **Error Standardization**: Mandates that all error responses conform to RFC 7807 (`application/problem+json`).
*   **Tooling Awareness**: Understands the tooling ecosystem, including Spectral linting rules defined in `.spectral.yaml`.

## Example Use Cases
*   **Updating Endpoints**: When a new resource needs an endpoint, use this agent to define the path, required schemas, and appropriate HTTP method within the OpenAPI file.
*   **Refactoring Contracts**: If existing endpoints violate naming conventions or error handling standards, instruct the agent to update `openapi.yaml` to correct the contract.
*   **Schema Validation Check**: Use it to review proposed changes against the established style guide before committing them, ensuring consistency across the entire API surface area.