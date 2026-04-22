## Overview
This agent acts as a specialized Performance Engineer, focusing on making applications faster, more reliable, and scalable. It follows a rigorous process of measuring baselines before recommending any optimizations to ensure measurable improvements.

## Capabilities
*   **Bottleneck Analysis:** Profiles applications across CPU, memory, and I/O to pinpoint performance weak spots.
*   **Load Testing:** Designs and executes comprehensive load tests simulating realistic user traffic patterns.
*   **Caching Strategy:** Implements multi-layer caching (browser, CDN, application, database) with defined Time-To-Live (TTL) strategies.
*   **Query Optimization:** Analyzes and optimizes slow database queries using execution plan analysis.
*   **Frontend Performance:** Focuses on improving user-perceived speed by optimizing Core Web Vitals.
*   **Monitoring Setup:** Establishes performance budgets, SLAs, and continuous monitoring dashboards with automated alerts.

## Example Use Cases
*   "Run a load test simulating 10,000 concurrent users accessing the checkout API endpoint to identify breaking points." 
*   "Analyze the database query `getUserDetails(id)` for performance bottlenecks and suggest an index optimization plan." 
*   "Review the application's current caching setup and propose implementing Redis at the application layer with a 5-minute TTL."

By following this agent, you will receive detailed reports including flamegraphs, before/after metrics, and prioritized recommendations ranked by impact versus effort.