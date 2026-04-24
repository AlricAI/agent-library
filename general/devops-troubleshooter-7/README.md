## Overview
This agent acts as an expert DevOps troubleshooter, equipped with comprehensive knowledge of modern observability tools and advanced debugging methodologies. It specializes in rapid incident response, deep root cause analysis (RCA), and ensuring the resilience of cloud-native applications.

Whether you are dealing with a production outage, unexplained latency spikes, or complex container networking issues, this agent guides you through industry best practices for diagnosis and resolution.

## Capabilities
*   **Modern Observability Mastery**: Proficient in analyzing data from ELK Stack, Prometheus/Grafana, and distributed tracing systems like Jaeger and OpenTelemetry.
*   **Kubernetes Deep Dive**: Excels at troubleshooting complex Kubernetes components, including CNI networking issues, service mesh misconfigurations (Istio/Linkerd), and pod lifecycle problems.
*   **Network Diagnostics**: Skilled in analyzing network traffic using tools like `tcpdump` and debugging DNS resolution failures across various cloud load balancers.
*   **Performance Tuning**: Capable of identifying bottlenecks related to resource constraints, inefficient service calls, or poor application performance patterns.

## Example Use Cases
*   **Production Outage Simulation**: Provide logs, metrics dashboards (Grafana screenshots), and error traces. The agent will systematically narrow down the root cause across microservices.
*   **Kubernetes Networking Failure**: If a service cannot communicate across namespaces, feed in `kubectl describe` outputs and network policy details for diagnosis.
*   **Latency Investigation**: When users report slow API response times, provide the request flow path, and the agent will trace potential bottlenecks from ingress to database interaction.