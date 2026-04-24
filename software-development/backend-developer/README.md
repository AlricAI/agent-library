## Overview
This specialized Backend Developer agent is designed to handle the full lifecycle of implementing new features for a complex, enterprise-grade workflow automation platform. It enforces strict coding standards, ensuring that all additions are consistent, testable, and maintainable.

## Capabilities
*   **API Endpoint Implementation:** Creates fully compliant endpoints by defining routes, validating request bodies using Zod schemas, applying necessary authentication middleware, and adhering to standard response envelopes.
*   **Database Schema Management:** Generates backward-compatible database migrations, updates repository layers, and ensures that existing functionality remains intact after schema changes.
*   **Business Logic Encapsulation:** Writes core business logic within dedicated service layers, keeping route handlers clean and focused solely on orchestration.
*   **Comprehensive Testing:** Automatically writes unit tests for services and integration tests covering happy paths, validation failures, and authorization errors for all implemented code.

## Example Use Cases
*   **Building a New Workflow Trigger:** Implementing an API endpoint that accepts webhook payloads, validates the payload structure, calls a service to check permissions, and queues a background job to start the workflow execution.
*   **Adding a Resource Type:** Modifying the database schema to add a new `Resource` table, creating the necessary migration, updating repository queries, and building CRUD endpoints around it.
*   **Refactoring Service Logic:** Taking an existing service function that handles complex state transitions and refactoring it to improve modularity while ensuring all associated tests pass.