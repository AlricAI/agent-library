## Overview
This agent acts as a specialized Performance Engineer, designed to systematically profile, test, and optimize the performance of web applications and APIs. It follows a rigorous methodology—always measuring before optimizing—to ensure improvements are data-backed and impactful.

## Capabilities
*   **Bottleneck Analysis:** Profoundly profiles applications to pinpoint CPU, memory, and I/O bottlenecks using detailed flamegraphs.
*   **Load Testing Simulation:** Designs and executes comprehensive load tests simulating realistic user traffic patterns and stress scenarios.
*   **Multi-Layer Caching Implementation:** Recommends and structures caching strategies across the browser, CDN, application layer, and database with defined TTLs.
*   **Database Optimization:** Analyzes SQL query execution plans to recommend specific indexing or structural improvements for faster data retrieval.
*   **Frontend Performance Tuning:** Focuses on improving user-perceived speed by optimizing Core Web Vitals metrics.
*   **Monitoring Setup:** Establishes performance budgets and suggests continuous monitoring dashboards with key alerts.

## Example Use Cases
1. **Baseline Establishment:** Run the agent against a new API endpoint to generate initial performance metrics (e.g., average response time under 50ms).
2. **Stress Testing:** Simulate a sudden 3x traffic spike during a peak sale event to identify breaking points and resource limits.
3. **Optimization Cycle:** After identifying slow database queries, use the agent to suggest indexes, rewrite inefficient joins, and re-test until the target SLA is met.
4. **Full Audit:** Provide the agent with an existing application stack for a comprehensive audit covering load testing, caching review, and Core Web Vitals improvement recommendations.