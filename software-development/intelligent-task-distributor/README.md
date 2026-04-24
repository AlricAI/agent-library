## Overview
This agent functions as a senior task distributor, specializing in the intelligent allocation of workloads across complex, distributed systems. Its core purpose is to maximize overall system throughput and efficiency by meticulously managing queues, balancing agent loads, and enforcing priority scheduling rules.

It moves beyond simple distribution methods (like round-robin) by analyzing real-time metrics—including capacity, performance history, and SLA requirements—to ensure tasks are routed optimally.

## Capabilities
*   **Advanced Load Balancing:** Implements various algorithms (e.g., weighted, least connections) with dynamic adjustment based on agent health checks and current utilization.
*   **Comprehensive Queue Management:** Handles priority levels, message ordering, Time-To-Live (TTL), and robust dead-letter queue management to prevent data loss.
*   **Intelligent Priority Scheduling:** Enforces strict Service Level Agreements (SLAs) and handles preemption rules while actively preventing task starvation.
*   **Capacity & Workload Tracking:** Continuously monitors agent performance metrics, resource usage, and skill mapping to make informed distribution decisions.
*   **Bottleneck Analysis:** Analyzes current distribution patterns against established checklists (e.g., latency targets, load variance) to suggest immediate optimizations.

## Example Use Cases
*   **High-Volume Microservices:** Distributing incoming API requests across a fleet of microservices while ensuring no single service becomes overloaded or falls below required response time thresholds.
*   **Asynchronous Job Processing:** Managing a queue of background jobs (e.g., image resizing, data ETL) by prioritizing critical tasks and dynamically assigning them to the least busy, most capable worker nodes.
*   **Real-Time Workflow Orchestration:** Implementing complex business workflows where task A must wait for Task B to complete on a specific resource type, requiring strict dependency management and failover handling.