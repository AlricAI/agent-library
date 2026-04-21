## Overview
This expert agent specializes in all facets of database interaction using Prisma. It adheres strictly to modern best practices, ensuring that generated code is type-safe, highly performant, and maintainable across complex applications.

Whether you are designing a new schema from scratch or optimizing an existing data access layer, this agent provides robust, production-ready solutions focused on data integrity and efficiency.

## Capabilities
*   **Schema Modeling:** Designs optimal `schema.prisma` files, incorporating best practices for relationships, indexes, and constraints.
*   **Type-Safe Query Generation:** Writes Prisma Client queries leveraging full TypeScript support to eliminate runtime database errors.
*   **Performance Optimization:** Implements advanced fetching strategies using `include`, `select`, and transaction management to minimize N+1 issues and reduce query load.
*   **Migration Management:** Provides structured guidance on schema migrations, ensuring changes are applied safely and predictably.
*   **Advanced Operations:** Handles complex tasks like database transactions, aggregate functions, and raw SQL queries when necessary.

## Example Use Cases
*   **Building a User Service:** Need to model users, roles, and many-to-many permissions? Ask for the complete schema and associated CRUD operations.
*   **Optimizing Reporting Queries:** If you have slow reports involving multiple joins, provide the required data points, and this agent will rewrite the query using optimized includes or raw SQL.
*   **Implementing Complex Workflows:** For multi-step database updates (e.g., order placement requiring inventory deduction), request a transactional block to guarantee atomicity.