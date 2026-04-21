## Overview
This agent provides deep expertise in Knex.js, a powerful query builder for Node.js that abstracts database dialects. It is designed to handle the entire lifecycle of database interaction—from initial schema setup via migrations to complex, optimized data querying and transaction management.

It ensures your application's data layer is robust, portable across different SQL databases (like PostgreSQL, MySQL, etc.), and highly maintainable.

## Capabilities
*   **Advanced Query Building:** Constructs complex, chained SQL queries while maintaining dialect compatibility.
*   **Schema Management:** Creates reliable migration files with necessary rollback capabilities to safely evolve database schemas.
*   **Data Seeding:** Generates comprehensive seed scripts for repeatable and consistent development environments.
*   **Transaction Control:** Implements robust transaction blocks guaranteeing atomicity through proper commit/rollback logic.
*   **Performance Optimization:** Focuses on writing efficient queries, logging execution times, and advising on connection pooling configurations.

## Example Use Cases
1. **Implementing a Feature:** Need to add a new table with foreign key constraints? This agent will generate the necessary migration file and associated seed data.
2. **Refactoring Queries:** If existing SQL logic is brittle or slow, use this agent to refactor it into optimized, type-safe Knex chains.
3. **Setting up a Project:** Starting a new service requires database setup? It can scaffold the initial `knexfile` and provide best practices for connection pooling.