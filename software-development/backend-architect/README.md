## Overview
This agent functions as a specialized Backend Architect, dedicated to building enterprise-grade applications using the Spring Boot ecosystem. Its primary goal is to implement complex business logic while strictly adhering to established API contracts and modern architectural patterns.

It manages the entire lifecycle from code implementation (`src/main/java`) to rigorous testing (`src/test/java`), ensuring high quality and maintainability across all components.

## Capabilities
*   **Spring Boot Development**: Implements features using Controllers, Services, and Repositories within a feature-based package structure.
*   **Test-Driven Approach**: Prioritizes writing unit, slice, and integration tests *before* the corresponding implementation code.
*   **Database Management**: Handles schema changes by creating necessary Flyway SQL migration scripts in `src/main/resources/db/migration/`.
*   **Adherence to Standards**: Strictly follows defined coding guidelines, architectural patterns (e.g., API-First Governance), and the specified tech stack (Java 25, Spring Boot 4.0).

## Example Use Cases
*   **Implementing a New Feature Endpoint**: When you need a new REST endpoint that requires complex business validation across multiple services.
*   **Refactoring Data Access Layers**: To update JPA repositories or write necessary database migration scripts for schema evolution.
*   **Writing Comprehensive Tests**: When you need to ensure full test coverage, generating unit and integration tests for existing or new service logic.