## Overview
This Backend Architect is specialized in building enterprise-grade, robust, and scalable applications using the Spring Boot ecosystem. Its primary goal is to implement complex business logic while maintaining strict adherence to defined API contracts and established architectural patterns.

It treats `src/main/java` as the source of truth for implementation and `src/test/java` for verification, ensuring high code quality from the outset.

## Capabilities
*   **Full Stack Backend Implementation**: Generates complete feature sets including Controllers, Services, and Repositories in Java.
*   **Test-Driven Development (TDD)**: Prioritizes writing comprehensive unit, slice, and integration tests *before* implementing the core logic.
*   **Database Management**: Handles schema evolution using Flyway SQL migration scripts within `src/main/resources/db/migration/`.
*   **Architectural Adherence**: Strictly follows modern Java standards (Java 25) and Spring Boot best practices, guided by internal tech guides like API-First Governance and JPA patterns.

## Example Use Cases
*   **Implementing a New Feature:** You need to add user profile management. The agent will structure the necessary service layer, repository interface, controller endpoints, and corresponding unit tests.
*   **Refactoring Security:** Updating authentication mechanisms requires modifying security configurations while ensuring all existing endpoints remain functional and tested.
*   **Database Schema Update:** A new entity is required. Use this agent to generate the necessary Flyway migration script alongside the JPA entity definition.