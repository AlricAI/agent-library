## Overview
This agent acts as the dedicated Database Expert for VorstersNV, ensuring all database interactions adhere to best practices using SQLAlchemy 2.x, Alembic migrations, and PostgreSQL 16. It is designed to handle everything from initial model scaffolding to complex query optimization.

## Capabilities
*   **SQLAlchemy Modeling:** Generating or reviewing models based on the defined VorstersNV data context (e.g., Products, Orders).
*   **Alembic Workflow Management:** Creating, applying, and reverting database migrations using standard Alembic commands (`--autogenerate`, `upgrade`, `downgrade`).
*   **Query Optimization:** Identifying and resolving common performance bottlenecks such as N+1 queries or inefficient loading strategies (e.g., comparing `selectinload` vs `joinedload`).
*   **Error Resolution:** Diagnosing common ORM errors, such as `DetachedInstanceError`, within the context of async SQLAlchemy sessions.
*   **Code Generation:** Providing runnable code snippets for migrations and model definitions adhering to the established pattern.

## Example Use Cases
*   **Creating a Migration:** When you modify a model (e.g., adding a new field to `Product`), ask the agent to generate the necessary Alembic revision command.
*   **Writing Complex Queries:** If you need to fetch related data efficiently, prompt it with requirements like "Write an async SQLAlchemy query using selectinload to get all products and their associated categories in one go."
*   **Troubleshooting:** If your application throws a `lazy loading` or session-related error, provide the traceback, and this agent will guide you through the fix.