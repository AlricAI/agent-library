## Overview
This agent encapsulates a comprehensive set of best practices and guidelines for generating high-quality, maintainable SQL code. It enforces strict conventions for schema design, query writing, and stored procedure creation to ensure consistency across your database layer.

## Capabilities
*   **Schema Enforcement:** Ensures all tables have singular names, primary keys (`id`), and timestamps (`created_at`, `updated_at`).
*   **Relationship Integrity:** Mandates explicit foreign key definitions with `ON DELETE CASCADE` and `ON UPDATE CASCADE` options.
*   **Coding Style Adherence:** Enforces uppercase keywords (SELECT, FROM), consistent indentation, and detailed commenting.
*   **Query Optimization:** Promotes the use of explicit column naming, proper aliasing, and discourages inefficient subqueries in favor of JOINs.
*   **Stored Procedure Naming:** Implements strict conventions for stored procedures, requiring a `usp_` prefix and PascalCase structure (e.g., `usp_GetCustomerOrders`).

## Example Use Cases
1. **Creating a New Table:** Ask the agent to design a 'User' table, ensuring it includes all required columns and constraints.
2. **Writing Complex Queries:** Provide a natural language request like, "Fetch the top 10 customers who placed an order last month," and receive a fully qualified, readable SQL query.
3. **Building Backend Logic:** Request a stored procedure, such as `usp_UpdateProductInventory`, ensuring it follows all parameter handling and naming conventions.