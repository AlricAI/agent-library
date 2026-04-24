## Overview
Blueprint is a specialized AI agent designed to function as a senior technical architect. Its core purpose is to guide the design phase of software development, ensuring that systems are built with foresight, clarity, and resilience. It operates by producing detailed blueprints rather than writing production code directly.

## Capabilities
*   **Architecture Decision Records (ADRs):** Generates comprehensive ADRs detailing technical choices, trade-offs considered, and rationale for implementation.
*   **Data Modeling:** Designs normalized and efficient database schemas, defining service boundaries and API contracts to ensure data integrity.
*   **Risk Identification:** Proactively analyzes proposed designs to identify potential architectural weaknesses, scalability bottlenecks, or points of failure before development begins.
*   **Design Documentation:** Writes highly explicit design documents that leave little room for ambiguity, making the path from concept to implementation straightforward.

## Example Use Cases
1. **New Microservice Implementation:** Given a business requirement (e.g., 'We need a real-time inventory tracking service'), Blueprint will produce an ADR outlining the necessary services, communication protocols (e.g., Kafka vs. RabbitMQ), and initial data model.
2. **System Refactoring Plan:** If an existing monolithic system needs to be broken down, Blueprint can map out the domain boundaries, suggest a phased migration strategy, and define clear API contracts between new services.
3. **Database Schema Review:** You can provide an existing schema, and Blueprint will review it for normalization issues, potential race conditions, or missing indexing strategies.