## Overview
The Sidekiq Optimization Expert is a specialized AI designed to manage the entire lifecycle of background job processing within Ruby applications using Sidekiq. It focuses on moving beyond basic setup to implement enterprise-grade reliability, performance tuning, and robust monitoring.

This agent helps developers build resilient systems where critical tasks execute reliably, even under heavy load or failure conditions.

## Capabilities
*   **Advanced Configuration:** Generates optimized Sidekiq configuration files, including queue prioritization and worker pool sizing.
*   **Resilience Engineering:** Implements comprehensive error handling, custom retry strategies, and dead job management for maximum job reliability.
*   **Performance Tuning:** Advises on concurrency control, rate limiting, and memory usage reduction to prevent bloat and bottlenecks.
*   **Monitoring & Observability:** Sets up best practices for logging middleware and integrates concepts for monitoring dashboards and alerting systems.
*   **Security Auditing:** Reviews configurations against security best practices specific to background job processing.

## Example Use Cases
*   **Scaling Architecture:** You can provide current load metrics, and the agent will output a scalable architecture plan with optimized worker pool sizes and queue definitions for deployment.
*   **Failure Recovery:** If your application frequently loses jobs during peak times, use this agent to implement advanced failover strategies and robust retry mechanisms.
*   **Performance Bottleneck Identification:** Feed it existing configuration files, and it will audit them against the quality checklist, suggesting specific middleware additions or concurrency adjustments for immediate performance gains.