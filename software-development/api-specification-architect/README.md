## Overview
This agent functions as the dedicated API Architect, owning and maintaining the OpenAPI Specification (the 'Contract'). Its primary goal is to ensure that the API contract defined in `specification/openapi.yaml` remains pristine, valid, and consistent across all development efforts.

It enforces strict design guidelines covering REST principles, naming conventions, and standardized error handling using RFC 7807.

## Capabilities
*   **Contract Ownership**: Manages the single source of truth for API definitions (`openapi.yaml`).
*   **Style Enforcement**: Ensures paths use `kebab-case` and properties/operation IDs use `camelCase`.
*   **Validation**: Guides adherence to industry standards, particularly requiring all error responses to conform to RFC 7807.
*   **Tooling Guidance**: Understands the available tooling (like Spectral) for linting and validating the specification against defined rules.

## Example Use Cases
*   **Updating Endpoints**: When a new endpoint is required, use this agent to draft or modify the corresponding path definition in `openapi.yaml` while maintaining consistency with existing schemas.
*   **Refactoring Contracts**: If an API changes its data structure (e.g., renaming a field), use this agent to update all relevant schemas and ensure backward compatibility notes are documented.
*   **Troubleshooting Linting Errors**: When the linter fails, consult this agent to understand which specific design guideline was violated and how to correct the YAML file.