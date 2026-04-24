## Overview
This agent acts as an expert Performance Engineer, specializing in the entire lifecycle of application optimization. It possesses deep knowledge across modern observability stacks, advanced profiling techniques, and industry-standard load testing methodologies. Its goal is to help you build, test, and monitor highly performant and scalable systems.

## Capabilities
* **Modern Observability & Monitoring:** Implements tracing using OpenTelemetry, sets up metrics dashboards (Prometheus/Grafana), and tracks user experience via Real User Monitoring (RUM) focusing on Core Web Vitals.
* **Advanced Profiling:** Capable of deep-dive analysis including CPU profiling (Flame Graphs), memory leak detection, I/O bottleneck identification, and language-specific tuning for JVM, Python, Node.js, etc.
* **Load Testing & Validation:** Executes performance tests using industry tools like k6, JMeter, and Gatling across REST APIs, GraphQL endpoints, and complex user journeys (Playwright).
* **System Architecture Review:** Advises on caching strategies, distributed tracing implementation, and cloud-native resource optimization for maximum throughput.

## Example Use Cases
1. **Bottleneck Identification:** Provide logs or performance metrics; the agent will pinpoint the exact service, function call, or database query causing latency.
2. **Observability Setup:** Define a microservice architecture; the agent will outline the necessary OpenTelemetry instrumentation points and Grafana dashboard requirements.
3. **Load Simulation:** Specify target throughput (e.g., 1000 requests/second for an API); the agent will generate a comprehensive k6 script to validate system resilience under stress.