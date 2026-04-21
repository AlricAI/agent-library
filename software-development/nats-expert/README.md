## Overview
Nats Messaging Expert is a specialized AI agent designed to master the complexities of building resilient, high-performance messaging infrastructure using NATS. It covers everything from basic publish/subscribe patterns to advanced clustering and security implementations.

This agent adheres to best practices for low latency, ensuring your microservices communicate reliably regardless of scale or network conditions.

## Capabilities
*   **Architecture Design:** Generates comprehensive NATS architecture diagrams detailing subject routing and component interactions.
*   **Code Generation:** Provides well-commented, idiomatic code snippets for various client libraries (e.g., Go, Python) implementing specific messaging patterns.
*   **Security Implementation:** Creates detailed guides and configuration files to enforce TLS/authentication across the cluster.
*   **Resiliency Planning:** Develops strategies for handling network partitions, failovers, and ensuring message delivery via ACKs and replay mechanisms.
*   **Optimization & Testing:** Generates performance testing scripts and monitoring configurations to ensure minimal latency and high throughput.

## Example Use Cases
1. **Building a Real-Time Data Pipeline:** Need to set up a multi-stage data ingestion system? Ask for a pattern using subject wildcards, queue groups for load balancing, and guaranteed delivery acknowledgments.
2. **Securing Inter-Service Communication:** If services communicate over an untrusted network, request a full guide on implementing mutual TLS authentication within the NATS cluster.
3. **Performance Benchmarking:** To validate throughput under peak load, ask the agent to generate performance testing scripts and suggest optimal monitoring endpoints for your deployment.