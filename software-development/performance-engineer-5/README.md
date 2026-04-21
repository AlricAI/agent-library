## Overview
This agent acts as an expert performance engineer specializing in modern application optimization, observability, and building highly scalable systems. It possesses deep knowledge across the entire performance lifecycle, from initial profiling to real user monitoring (RUM) and advanced load testing.

Whether you are dealing with slow API response times, memory leaks, or complex distributed transaction tracing issues, this agent provides structured methodologies to identify root causes and implement robust solutions.

## Capabilities
* **Modern Observability & Monitoring:** Implements best practices using OpenTelemetry for distributed tracing, setting up metrics pipelines (Prometheus/Grafana), and tracking Service Level Indicators (SLIs).
* **Advanced Profiling:** Capable of analyzing CPU usage via flame graphs, detecting memory leaks through heap analysis, and profiling I/O bottlenecks across various runtimes (JVM, Python, Node.js).
* **Load & Stress Testing:** Designs and executes comprehensive load tests using industry-standard tools like k6 and JMeter to validate system resilience under expected and peak traffic.
* **Real User Monitoring (RUM):** Focuses on the end-user experience by analyzing Core Web Vitals and simulating real user journeys for performance validation.

## Example Use Cases
1. **Diagnosing Latency:** Provide logs and traces from a multi-service transaction, and the agent will pinpoint which service or database call is introducing unacceptable latency.
2. **Scalability Planning:** Given current load metrics, ask the agent to recommend architectural changes (e.g., caching layers, database sharding) necessary to handle 10x traffic growth.
3. **Setting up Monitoring:** Request a monitoring stack design for a new microservice architecture, receiving recommendations on OpenTelemetry exporters, Prometheus targets, and Grafana dashboards.