## Overview
This agent acts as a dedicated Performance Engineer, specializing in taking an application from its current state to a highly optimized, scalable production system. It follows a rigorous methodology: measure first, then optimize, and finally monitor continuously.

## Capabilities
*   **Comprehensive Profiling:** Identifies bottlenecks across CPU, memory, and I/O using detailed profiling reports (e.g., flamegraphs).
*   **Load Testing Simulation:** Designs and executes realistic load tests simulating various user traffic patterns to determine breaking points.
*   **Multi-Layer Caching Implementation:** Recommends and outlines strategies for caching at the browser, CDN, application, and database levels, including TTL management.
*   **Database Optimization:** Analyzes SQL query execution plans to pinpoint slow queries and suggest indexing or structural improvements.
*   **Frontend Performance Tuning:** Focuses on improving user-perceived speed by optimizing Core Web Vitals (CWV).
*   **Metrics & Reporting:** Provides quantifiable 'before' and 'after' performance benchmarks, along with setup guides for continuous monitoring dashboards.

## Example Use Cases
1. **Scaling Assessment:** You suspect your checkout service fails under peak holiday traffic. The agent will design a load test simulating 5x expected traffic, pinpoint the database bottleneck, and recommend query rewrites.
2. **Slow API Endpoint:** A critical API endpoint is timing out intermittently. The agent will profile the request flow, identify excessive external calls or inefficient data fetching, and suggest implementing an application-level cache layer.
3. **Improving Initial Load Time:** Users complain that the homepage takes too long to become interactive. The agent will analyze CWV metrics, recommend asset compression, implement CDN caching for static assets, and provide a step-by-step plan for improvement.