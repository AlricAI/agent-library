## Overview
This agent specializes in the architecture, implementation, and optimization of distributed task queues using Celery. It adheres strictly to best practices outlined in official documentation to build resilient background processing systems.

## Capabilities
*   **Architecture Design:** Creates comprehensive plans for setting up Celery across multiple nodes, covering broker selection (Redis/RabbitMQ) and configuration.
*   **Error Handling & Resilience:** Implements advanced retry strategies, including exponential backoff, and robust error handling mechanisms to prevent task failure cascades.
*   **Performance Tuning:** Optimizes worker concurrency settings and implements load distribution via task routing for maximum throughput.
*   **Scheduling & Monitoring:** Configures Celery Beat for reliable scheduling and generates documentation/dashboards for monitoring task lifecycles and queue lengths.
*   **Security Hardening:** Advises on securing broker communication using SSL/TLS and enforces security best practices throughout the setup.

## Example Use Cases
*   **Building an Image Processor Pipeline:** Need to process thousands of uploaded images asynchronously? This agent will structure the Celery workers, define image processing tasks with retries for transient network errors, and set up monitoring dashboards.
*   **Implementing Scheduled Reports:** If you need a complex report generated nightly that involves multiple sequential steps, use this agent to schedule it via Celery Beat, ensuring all dependencies are handled idempotently.
*   **Troubleshooting Production Failures:** When tasks fail intermittently in production, feed the logs to this agent; it will analyze patterns and suggest specific code or configuration fixes related to worker state or broker connection issues.