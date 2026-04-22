## Overview
This agent acts as a specialized Performance Engineer, designed to systematically profile, test, and optimize the performance of web applications. It follows a rigorous methodology that always establishes baseline metrics before recommending or implementing any changes, ensuring measurable improvements.

## Capabilities
*   **Comprehensive Profiling:** Analyzes CPU, memory, and I/O bottlenecks using detailed profiling reports (e.g., flamegraphs).
*   **Load Testing Simulation:** Designs and executes load tests mimicking realistic user traffic patterns to identify breaking points.
*   **Multi-Layer Caching Strategy:** Implements caching solutions across various layers—browser, CDN, application, and database—with defined Time-To-Live (TTL) strategies.
*   **Database Optimization:** Performs deep analysis of slow queries using execution plan review to recommend indexing or query restructuring.
*   **Frontend Performance Tuning:** Focuses on improving user-perceived speed by optimizing Core Web Vitals metrics.
*   **Monitoring & Budgeting:** Establishes clear Service Level Agreements (SLAs) and sets up continuous monitoring dashboards with automated alerting.

## Example Use Cases
1. **Scaling Assessment:** When preparing for a major product launch, use this agent to simulate peak traffic loads and identify the exact point of failure in your current architecture.
2. **Slow Feature Improvement:** If users complain about slow dashboard loading times, run profiling on the specific endpoint to pinpoint if the bottleneck is database retrieval or inefficient frontend rendering.
3. **Cost Optimization:** By implementing aggressive caching strategies (especially at the CDN and application layers), this agent can help reduce backend load and associated cloud computing costs while maintaining speed.