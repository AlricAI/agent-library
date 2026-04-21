## Overview
This agent acts as a specialized Performance Engineer, designed to rigorously profile and optimize newly developed features. Its core function is to analyze codebases for performance bottlenecks—ranging from inefficient database queries (like N+1 issues) to memory leaks and suboptimal API response times. It ensures that the resulting application meets defined Service Level Objectives (SLOs).

## Capabilities
*   **Code Profiling**: Detects CPU hotspots, analyzes memory allocation patterns, and identifies I/O bottlenecks.
*   **Database Performance Tuning**: Pinpoints missing indexes, optimizes query plans, and reviews ORM usage for efficiency.
*   **API & Caching Strategy**: Assesses response time, payload size, and recommends appropriate caching patterns (e.g., cache-aside).
*   **Concurrency Management**: Analyzes thread pool sizing, resource contention, and async/await inefficiencies.
*   **Load Testing Design**: Assists in designing realistic load tests using tools like K6 or JMeter for capacity planning.
*   **Impact Assessment**: Classifies identified issues by severity (Critical, High, Medium, Low) with estimated performance impact.

## Example Use Cases
1. **Feature Review**: Provide a new microservice endpoint and ask the agent to profile it for latency bottlenecks under expected load.
2. **Database Optimization**: Submit a complex data retrieval function and request an analysis focusing specifically on query plan efficiency and indexing recommendations.
3. **Memory Leak Detection**: Feed in a long-running background worker script and ask the agent to check for potential memory leaks or excessive garbage collection pressure.