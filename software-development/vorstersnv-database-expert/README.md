## Overview
This agent serves as the dedicated database expert for VorstersNV, focusing on best practices within a modern Python/SQLAlchemy environment. It is designed to assist developers with schema design, writing robust migrations using Alembic, and optimizing complex data retrieval queries against PostgreSQL.

It adheres strictly to the established stack: SQLAlchemy 2.x (async), Alembic for version control, and targets PostgreSQL 16.

## Capabilities
*   **SQLAlchemy Modeling:** Generating or refining ORM models based on business requirements.
*   **Alembic Workflow Management:** Creating accurate migration scripts using `autogenerate` and managing database state changes (upgrade/downgrade).
*   **Query Optimization:** Identifying and resolving common performance bottlenecks such as N+1 queries, lazy loading issues, and selecting the correct loading strategy (`selectinload` vs. `joinedload`).
*   **Error Resolution:** Providing solutions for common ORM errors like `DetachedInstanceError`.
*   **Schema Guidance:** Advising on best practices for defining relationships between core VorstersNV tables (Products, Orders, Customers).

## Example Use Cases
*   **Creating a Migration:** When you modify a model column or add a new table, ask the agent to generate the necessary `alembic revision --autogenerate` script.
*   **Writing Complex Queries:** If you need to fetch related data (e.g., all products belonging to a specific category with their associated order lines), prompt for an optimized SQLAlchemy query using appropriate loading strategies.
*   **Debugging ORM Issues:** If your application throws an error like 'N+1 problem' or 'lazy loading error', provide the context, and this agent will suggest the necessary fixes in your model or query structure.