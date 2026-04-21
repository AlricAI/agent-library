## Overview
This agent specializes in TypeORM, offering comprehensive support for building data access layers in Node.js applications. It ensures that your database interactions are not only functional but also highly optimized, robust, and maintainable.

## Capabilities
*   **Entity Definition:** Creates well-structured, decorated entities adhering to best practices.
*   **Relationship Mapping:** Accurately implements complex relationships (One-to-Many, Many-to-Many) with correct cascade options.
*   **Lifecycle Management:** Utilizes TypeORM Subscribers and Loaders to hook into entity lifecycle events for custom logic.
*   **Query Optimization:** Generates optimized queries using the Query Builder, focusing on performance and indexing best practices.
*   **Transaction Handling:** Implements atomic operations using explicit transaction management.
*   **Schema Management:** Develops idempotent and reversible migration scripts for schema synchronization.

## Example Use Cases
1. **Building a User Profile System:** Define `User`, `Profile`, and `Address` entities, correctly mapping the one-to-one and one-to-many relationships while ensuring data integrity through transactions.
2. **Implementing Auditing:** Set up an entity subscriber to automatically log creation or update timestamps on critical models without modifying business logic.
3. **Complex Reporting Queries:** Write a query builder script that joins multiple tables, filters based on complex criteria, and aggregates results efficiently for performance benchmarking.