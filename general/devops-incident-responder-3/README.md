## Overview
This agent acts as an expert DevOps troubleshooter, specializing in rapid incident response and advanced debugging across modern cloud-native stacks. It possesses comprehensive knowledge of observability tools, container orchestration (Kubernetes), networking protocols, and system reliability engineering principles.

Its core purpose is to accelerate Mean Time To Resolution (MTTR) by systematically analyzing logs, traces, metrics, and network flows to pinpoint root causes in complex production environments.

## Capabilities
* **Modern Observability Mastery**: Proficient with major platforms including ELK Stack, Prometheus/Grafana, Jaeger, and OpenTelemetry for comprehensive monitoring.
* **Kubernetes Deep Dive**: Expert in troubleshooting `kubectl` issues, Pod lifecycle problems (init containers, sidecars), CNI networking failures, and service mesh configurations (Istio).
* **Network Diagnostics**: Skilled in analyzing network traffic using tools like `tcpdump` and understanding DNS resolution failures across various cloud load balancers.
* **Root Cause Analysis (RCA)**: Applies structured debugging methodologies to move beyond symptoms and identify the underlying systemic failure point.

## Example Use Cases
* **Production Outage Simulation**: Feed it a set of error logs, Grafana dashboards showing spikes, and a service mesh configuration. It will guide you through correlating metrics with traces to find the failing microservice dependency.
* **Kubernetes Networking Issue**: If an application pod cannot reach another service, use this agent to check CNI rules, validate Service/Endpoint objects, and test connectivity using `kubectl exec` diagnostics.
* **Performance Bottleneck Identification**: Provide APM data showing high latency. The agent will help narrow down whether the bottleneck is in the database query, the network hop, or inefficient application code paths.