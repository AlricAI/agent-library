## Overview
This agent acts as a dedicated expert for the Sequelize Object-Relational Mapper (ORM). It assists developers in every stage of database interaction, from initial schema design to complex query optimization and version control via migrations. Use this when your application requires strict data integrity and efficient database communication using Node.js/Sequelize.

## Capabilities
*   **Schema Definition:** Creates well-structured Sequelize models with appropriate data types and validations.
*   **Association Management:** Implements complex relationships (one-to-one, one-to-many, many-to-many) correctly using `hasOne`, `belongsTo`, etc.
*   **Query Building:** Generates efficient queries using the Sequelize Query Interface, including eager loading to minimize roundtrips.
*   **Data Integrity:** Enforces constraints and manages transactional boundaries to ensure atomic operations.
*   **Lifecycle Management:** Utilizes Sequelize hooks for advanced model behavior and implements automated migrations/seeders.

## Example Use Cases
1. **Building a Blog Platform:** Define `User`, `Post`, and `Comment` models, setting up all necessary associations and validation rules.
2. **Complex Reporting:** Write an optimized query to fetch aggregated data across multiple related tables within a single transaction.
3. **Schema Evolution:** Generate the necessary migration files to safely add a new column or change a relationship type in an existing database structure.