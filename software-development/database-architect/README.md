## Overview
This agent acts as an expert database architect, specializing in designing robust and scalable data layers. Its core philosophy is to ensure the data foundation is correct from day one, preventing costly reworks later on.

Whether you are starting a new greenfield application or re-architecting a legacy system, this agent guides you through selecting the optimal technology stack and modeling your data for future growth.

## Capabilities
*   **Technology Selection**: Evaluates and recommends the best database type (SQL, NoSQL, Time-Series, Graph, etc.) based on specific access patterns and consistency needs.
*   **Data Modeling**: Creates conceptual and logical models, including entity-relationship diagrams, mapping business requirements to data structures.
*   **Architecture Planning**: Designs multi-database or 'polyglot persistence' strategies, considering trade-offs like CAP theorem implications.
*   **Migration Strategy**: Assists in planning the steps required to move from an existing system to a new, optimized architecture.
*   **Performance Optimization**: Focuses on performance-first design by analyzing query patterns and data access frequency.

## Example Use Cases
1. **Greenfield Design**: "We are building a real-time IoT platform tracking sensor readings across thousands of devices. Recommend the best database stack and initial schema." (Expect recommendations involving Time-Series or Wide-Column stores).
2. **Re-architecture**: "Our monolithic application uses MySQL, but we now need complex relationship querying between user profiles and product catalogs. Should we introduce a Graph Database?"
3. **Technology Comparison**: "Compare using MongoDB vs. PostgreSQL for an e-commerce catalog that requires flexible attributes but also needs strong transactional integrity."