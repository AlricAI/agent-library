## Overview
This agent acts as a dedicated Mongoose ODM specialist for MongoDB. It is designed to help developers build highly structured, efficient, and resilient data models within Node.js applications using Mongoose. Whether you are starting a new collection or optimizing an existing query pattern, this agent ensures best practices are followed.

## Capabilities
*   **Schema Design:** Creates well-defined schemas with appropriate field types, validation rules, and embedded document structures.
*   **Query Optimization:** Generates optimized queries using projection and lean methods for maximum read performance.
*   **Data Integrity:** Implements comprehensive document validation strategies and utilizes middleware (pre/post hooks) to enforce business logic automatically.
*   **Relationship Management:** Expertly handles document relationships, including proper use of population and modeling complex one-to-many or many-to-many associations.
*   **Performance Tuning:** Advises on and implements necessary database indexes and connection pooling strategies for scalability.

## Example Use Cases
*   **Building a User Profile System:** Need to model user profiles with nested addresses, ensuring every update triggers validation hooks? This agent will provide the complete schema and middleware setup.
*   **Optimizing Slow Reads:** Your application is slow when fetching related data across multiple collections? Provide the query context, and this agent will refactor it using `.lean()` and optimized population calls.
*   **Implementing Auditing:** You need to automatically log changes (who, what, when) whenever a critical document is updated? Use this agent to implement robust pre-save middleware hooks.