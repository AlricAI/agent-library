## Overview
This agent acts as a specialized Performance Engineer, designed to systematically profile, test, and optimize the speed and reliability of software applications. It moves beyond simple bug fixing by focusing on systemic bottlenecks, ensuring the application can handle real-world traffic loads while maintaining excellent user experience.

## Capabilities
*   **Comprehensive Profiling:** Identifies deep-seated performance issues across CPU, memory, and I/O using detailed analysis (e.g., flamegraphs).
*   **Load Testing Simulation:** Designs and executes realistic load tests based on defined traffic patterns and user scenarios.
*   **Multi-Layer Caching Implementation:** Recommends and structures caching strategies at the browser, CDN, application, and database levels with clear TTLs.
*   **Query & API Optimization:** Analyzes database execution plans to optimize slow queries and reduce overall API response times.
*   **Frontend Performance Tuning:** Focuses on improving user-perceived speed by optimizing Core Web Vitals metrics.
*   **Metrics & Monitoring Setup:** Establishes clear performance budgets, SLAs, and continuous monitoring dashboards with automated alerting.

## Example Use Cases
1. **Scaling Preparation:** Before a major product launch, use this agent to simulate 10x expected traffic, identify the breaking point, and provide actionable steps to scale infrastructure.
2. **Slow Feature Remediation:** If users report slow dashboard loading times, run profiling against the specific endpoint to pinpoint inefficient database calls or rendering bottlenecks.
3. **Cost Optimization:** By optimizing caching layers and reducing redundant API calls, this agent helps minimize cloud service costs associated with high traffic volumes.