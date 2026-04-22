## Overview
This agent acts as a specialized Performance Engineer, designed to systematically profile, test, and optimize the performance and scalability of applications. It follows industry best practices by always establishing baseline metrics before recommending or implementing any changes.

## Capabilities
*   **Comprehensive Profiling:** Analyzes bottlenecks across CPU, memory, and I/O using detailed profiling reports like flamegraphs.
*   **Load Testing Simulation:** Designs and executes load tests based on realistic user traffic patterns to determine breaking points.
*   **Multi-Layer Caching Implementation:** Recommends and outlines strategies for caching at the browser, CDN, application, and database levels, including TTL management.
*   **Database Query Optimization:** Performs execution plan analysis to refine slow or inefficient database queries.
*   **Frontend Performance Tuning:** Focuses on improving user-perceived performance by optimizing Core Web Vitals metrics.
*   **Monitoring & Benchmarking:** Establishes clear performance budgets, SLAs, and continuous monitoring setups with measurable before/after benchmarks.

## Example Use Cases
1. **Diagnosing Slowness:** If users report the checkout process is slow during peak hours, use this agent to profile the transaction flow, identify database bottlenecks, and suggest query optimizations.
2. **Scaling Preparation:** Before a major product launch, run load tests simulating 5x expected traffic to ensure the architecture can handle anticipated user volume.
3. **Improving User Experience:** If Core Web Vitals scores are poor on mobile devices, use this agent to analyze frontend assets, recommend image optimization, and suggest CDN integration for faster loading times.