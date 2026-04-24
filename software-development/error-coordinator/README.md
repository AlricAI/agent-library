## Overview
The Error Coordinator is a senior specialist agent designed to manage the lifecycle of system failures in complex, distributed environments. Its core function is to move systems beyond simple error detection toward true anti-fragility by systematically analyzing, correlating, and orchestrating recovery from failures.

It operates on principles derived from advanced resilience patterns, ensuring that when one component fails, the entire system does not collapse. It continuously learns from every incident to improve future stability.

## Capabilities
*   **Error Aggregation & Classification:** Collects raw error data into structured taxonomies, assessing severity and impact across all services.
*   **Cross-Agent Correlation:** Identifies root causes by analyzing temporal relationships, causal chains, and service dependencies between multiple failing components.
*   **Failure Cascade Prevention:** Implements advanced patterns like Circuit Breakers, Bulkheads, and Rate Limiting to isolate failures before they spread.
*   **Recovery Orchestration:** Executes automated, multi-step recovery flows, including state restoration, rollback procedures, and gradual service reintroduction.
*   **Resilience Auditing:** Verifies system health against strict metrics (e.g., MTTR < 5 minutes, Cascade Prevention = 100%).

## Example Use Cases
*   **Microservice Outage Simulation:** When a critical payment microservice fails intermittently, the agent detects the pattern, trips circuit breakers on dependent services, and orchestrates a controlled rollback to the last known stable state while alerting necessary teams.
*   **High-Volume Traffic Spike:** During unexpected load spikes, the agent proactively manages backpressure by shedding non-critical requests (load shedding) rather than allowing all services to time out simultaneously, thus maintaining core functionality.
*   **Dependency Failure Analysis:** If Service A fails due to a dependency issue in Service B, the coordinator traces the error backward through request tracing logs to pinpoint the exact failing boundary condition and suggests an immediate patch or temporary fallback mechanism.