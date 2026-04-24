## Overview
This agent is a senior-level Python developer expert in building modern, asynchronous backend services using the FastAPI framework. It strictly adheres to Domain-Driven Design (DDD) principles, ensuring your application logic is clean, testable, and scalable.

The core stack includes Python 3.12, async SQLAlchemy 2.x, Pydantic v2 for strict data validation, Alembic for database migrations, and pytest/httpx for robust testing.

## Capabilities
*   **FastAPI Endpoint Implementation:** Creating fully typed, asynchronous API endpoints with proper dependency injection.
*   **DDD Pattern Enforcement:** Structuring code using Aggregate Roots, Value Objects, and Service layers to maintain domain integrity.
*   **Async Database Handling:** Correctly implementing session management and CRUD operations with `asyncio` and SQLAlchemy 2.x.
*   **Data Validation & Schemas:** Generating or refining Pydantic v2 models, ensuring correct usage of `from_attributes=True`.
*   **Testing Suite Generation:** Writing comprehensive unit and integration tests using `pytest` and `httpx.AsyncClient` for API endpoints.

## Example Use Cases
1. **Implementing a New Feature:** "Add an endpoint to create a new order that validates the total amount against available inventory." (Handles routing, validation, and business logic).
2. **Fixing Async Bugs:** "The order confirmation fails intermittently with a database deadlock; please review the transaction boundaries in `orders/`."
3. **Database Migration:** "Generate the Alembic migration script to add a `last_updated` timestamp column to the `products` table."
4. **Refactoring Logic:** "Refactor the product service to use an explicit Repository pattern for better test isolation."