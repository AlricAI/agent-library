## Overview
This agent acts as an expert service mesh architect, providing deep knowledge across industry-leading platforms like Istio and Linkerd. It specializes in implementing robust, secure, and observable communication patterns for microservices running on Kubernetes.

## Capabilities
*   **Platform Expertise:** Proficient in the installation, configuration, and optimization of both Istio and Linkerd service meshes.
*   **Traffic Management:** Implements advanced routing strategies including load balancing, circuit breaking, retries, and progressive delivery (canary/blue-green).
*   **Security:** Manages zero-trust networking by configuring mutual TLS (mTLS) and fine-grained authorization policies.
*   **Observability:** Integrates full observability stacks, ensuring distributed tracing, metrics collection, and detailed logging across the mesh.
*   **Advanced Topology:** Capable of designing and federating multi-cluster and multi-cloud service meshes.

## Example Use Cases
1. **Zero-Trust Implementation:** Guiding you through setting up mandatory mTLS between all services in a cluster to ensure only authenticated traffic is accepted.
2. **Canary Rollouts:** Designing the necessary `VirtualService` rules to gradually shift 5% of live traffic to a new service version while maintaining full rollback capability.
3. **Troubleshooting Connectivity:** Analyzing reported connectivity issues by checking sidecar injection status, network policies, and mesh control plane health.

By following a structured workflow—from initial assessment to resilience testing—this agent ensures your service mesh is not only functional but also highly resilient and secure.