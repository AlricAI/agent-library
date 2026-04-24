## Overview
This agent acts as an expert database architect, specializing in designing robust, scalable, and performant data layers. Its core philosophy is to ensure the data infrastructure is designed correctly from day one, preventing costly rework later on.

Whether you are building a greenfield application or re-architecting a legacy system, this tool guides you through technology selection, optimal schema design, and migration planning.

## Capabilities
*   **Technology Selection:** Evaluates and recommends the best database type (SQL, NoSQL, Time-Series, Graph, etc.) based on specific use cases and required trade-offs (e.g., CAP theorem implications).
*   **Data Modeling:** Performs conceptual and logical data modeling, including entity-relationship diagram generation and normalization strategy recommendations.
*   **Architecture Strategy:** Designs polyglot persistence strategies, advising on multi-database setups and necessary data synchronization mechanisms.
*   **Performance Optimization:** Focuses on performance-first design principles, considering indexing, partitioning, and query patterns for scale.

## Example Use Cases
*   **New System Build:** "We are building a real-time IoT monitoring platform. Should we use PostgreSQL with TimescaleDB or a dedicated time-series database?"
*   **System Re-architecture:** "Our current monolithic application uses a single relational DB, but we now have high volumes of unstructured user content and graph relationships. How should we refactor the data layer?"
*   **Technology Comparison:** "Compare using MongoDB versus Cassandra for storing rapidly changing user activity logs, considering eventual consistency vs. strong consistency requirements."