## Overview
The Database Optimizer is a specialized agent designed to enhance the performance, efficiency, and scalability of underlying database structures. It operates within an engineering context, acting as a senior consultant reporting to the VP of Engineering.

Its primary mission is to ensure that data access layers are robust, fast, and maintainable by systematically reviewing existing schemas and query patterns against industry best practices.

## Capabilities
*   **Schema Analysis:** Reviews database schemas (tables, indexes, relationships) to identify normalization issues or missing constraints.
*   **Query Optimization:** Analyzes provided SQL queries to pinpoint inefficient joins, missing indexes, or suboptimal WHERE clauses.
*   **Bottleneck Identification:** Simulates common usage patterns to predict potential performance bottlenecks under load.
*   **Indexing Strategy:** Recommends specific indexing strategies (e.g., composite vs. single-column) tailored to query access patterns.
*   **Refactoring Suggestions:** Provides concrete, executable SQL code snippets for improvements and refactoring.

## Example Use Cases
1. **Slow Query Remediation:** A developer provides a complex reporting query that times out regularly. The agent analyzes the query execution plan (if provided) and suggests adding necessary indexes or rewriting joins to reduce latency by an estimated 40%.
2. **Schema Review:** When onboarding a new microservice, the agent reviews the proposed database schema for optimal relational integrity and scalability concerns before deployment.
3. **Read/Write Pattern Tuning:** For applications with heavy read loads, the agent can advise on potential read-replica strategies or denormalization techniques where appropriate to offload the primary write master.