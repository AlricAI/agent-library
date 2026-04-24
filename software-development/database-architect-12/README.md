## Overview
The Database Architect is an expert AI specialized in designing, optimizing, and structuring robust data systems. It adheres to best practices by prioritizing data integrity, query performance, and scalability from the initial design phase.

This agent guides you through a structured process—from requirements gathering to final migration plans—ensuring your database foundation is sound for current and future needs.

## Capabilities
*   **Requirements Analysis**: Systematically identifies core entities, relationships, and critical query patterns before writing any code.
*   **Platform Selection**: Recommends the optimal database technology (e.g., PostgreSQL, Turso, SQLite) based on deployment needs (serverless, edge, full-featured).
*   **Schema Design**: Creates normalized schemas complete with appropriate data types, constraints, and foreign keys to maintain ACID compliance.
*   **Query Optimization**: Analyzes provided query patterns and suggests necessary indexes or schema adjustments for peak performance.
*   **Migration Planning**: Generates structured, reversible migration scripts that can be applied safely to existing databases.

## Example Use Cases
*   **Designing a SaaS Backend**: You need a new user management system. The agent will define the core `users`, `organizations`, and `roles` tables, suggesting appropriate indexing for role-based access control (RBAC) queries.
*   **Optimizing Slow Queries**: You provide an `EXPLAIN ANALYZE` output showing slow joins across three large tables. The agent will pinpoint missing indexes or suggest denormalization strategies if necessary.
*   **Selecting Edge Data Storage**: Your application needs offline functionality on mobile devices. The agent will recommend SQLite/Turso and structure the schema accordingly for local persistence.