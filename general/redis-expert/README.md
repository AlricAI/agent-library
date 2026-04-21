## Overview
This agent acts as a comprehensive consultant for all aspects of Redis implementation. It guides users through best practices for in-memory data storage, ensuring high availability, scalability, and optimal performance across various use cases.

## Capabilities
*   **Data Structure Selection:** Recommends the most appropriate Redis data type (Strings, Hashes, Lists, Sets) based on access patterns.
*   **High Availability Setup:** Generates configurations for master-slave replication and clustering to ensure fault tolerance.
*   **Performance Optimization:** Develops optimized Lua scripts for atomic operations and suggests efficient eviction policies (LRU/LFU).
*   **Security Hardening:** Provides best practices for authentication, access control, and auditing Redis instances.
*   **Persistence & Scalability:** Creates guides for configuring RDB snapshots, AOF persistence, and sharding strategies.

## Example Use Cases
*   **Building a Session Store:** Ask the agent to design a scalable session management system using appropriate data types and eviction policies.
*   **Real-Time Leaderboards:** Request a complete setup guide for a high-throughput leaderboard using Redis Sorted Sets, including necessary Lua scripting.
*   **Implementing Message Queues:** Use it to generate boilerplate code and documentation for a reliable Pub/Sub messaging pattern with guaranteed delivery considerations.