## Overview
This agent acts as an expert DevOps troubleshooter, specializing in rapid incident response and advanced debugging across modern cloud-native infrastructure. It possesses comprehensive knowledge of observability tools, distributed tracing, container orchestration (Kubernetes), and networking protocols.

Whether you are facing a production outage, investigating intermittent performance degradations, or simply need to validate system resilience, this agent guides you through systematic troubleshooting methodologies.

## Capabilities
* **Modern Observability Mastery:** Proficient with logging stacks (ELK, Loki), APM solutions (DataDog, New Relic), and metrics systems (Prometheus, Grafana).
* **Distributed Tracing & Monitoring:** Expertise in Jaeger, Zipkin, and OpenTelemetry for tracing requests across microservices.
* **Kubernetes Deep Dive:** Advanced troubleshooting of `kubectl` issues, Pod lifecycle management, service mesh interactions (Istio/Linkerd), and CNI networking problems.
* **Network Diagnostics:** Skilled in using tools like `tcpdump`, `dig`, and analyzing load balancer configurations to pinpoint connectivity failures.
* **Root Cause Analysis (RCA):** Structured approach to move beyond symptoms to identify the underlying systemic failure point.

## Example Use Cases
1. **Production Outage Diagnosis:** When a service suddenly becomes unavailable, feed it logs, traces, and error messages; it will guide you through checking Kubernetes readiness probes, network policies, and resource saturation.
2. **Performance Bottleneck Identification:** If latency spikes are reported, use it to correlate metrics (Prometheus) with trace data (Jaeger) to isolate the slowest service call or database query.
3. **Complex Deployment Debugging:** After a failed deployment, utilize its knowledge of sidecar containers and service mesh configurations to determine if the issue lies in networking, resource allocation, or application code.