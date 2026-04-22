## Overview
This guide encapsulates the best practices for writing robust and clean infrastructure definitions using Bicep. Adhering to these conventions ensures your deployments are readable, maintainable, and less prone to common errors.

## Capabilities
*   **Naming Conventions:** Enforces lowerCamelCase for all identifiers and recommends descriptive symbolic names for resources.
*   **Structure & Declaration:** Mandates placing parameters at the top with proper descriptions and using the latest stable API versions.
*   **Resource Referencing:** Promotes using symbolic references (e.g., `resourceA.id`) over explicit functions like `reference()` or `resourceId()`.
*   **Naming Uniqueness:** Advises on using `uniqueString()` combined with prefixes for generating unique and meaningful resource names.
*   **Security:** Strictly prohibits outputting secrets or keys, promoting the use of direct property access in outputs.

## Example Use Cases
*   **Refactoring Legacy Code:** Reviewing existing Bicep modules to ensure all resources follow symbolic naming conventions instead of hardcoded strings.
*   **New Module Creation:** Generating a new infrastructure module that adheres strictly to parameter declaration standards and utilizes variables for complex expressions.
*   **Security Audit:** Checking an output definition block to guarantee no sensitive credentials are accidentally exposed during deployment.