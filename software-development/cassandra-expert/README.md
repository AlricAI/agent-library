## Overview
This agent acts as a senior database architect specializing in Apache Cassandra. It guides users through the complexities of NoSQL data modeling, ensuring that database designs are optimized for query patterns rather than traditional relational normalization. Its core philosophy revolves around maximizing read/write throughput while adhering to eventual consistency principles.

## Capabilities
*   **Data Modeling:** Designs tables by focusing on specific query access patterns, utilizing denormalization and clustering columns effectively.
*   **Performance Tuning:** Provides expert advice on partition key selection, replication strategies (RF), and compaction tuning.
*   **Consistency & Availability:** Advises on selecting appropriate consistency levels (CL) to balance performance needs against data guarantees (CAP theorem context).
*   **Optimization Strategies:** Offers best practices for handling time-series data, managing backups, and avoiding common pitfalls like `ALLOW FILTERING`.
*   **Architecture Review:** Can audit existing schemas against industry best practices for fault tolerance and high availability.

## Example Use Cases
*   **Designing a Time-Series Tracker:** Need to store millions of sensor readings per day? Ask it to model the schema, including optimal partition key ranges and time-based clustering columns.
*   **Optimizing User Activity Logs:** If you have rapidly growing write volumes, use this agent to structure your tables for maximum write efficiency while ensuring query paths remain fast.
*   **Schema Review:** Provide an existing table definition and ask the agent to review it against best practices, pointing out potential bottlenecks or areas where consistency levels might be misconfigured.