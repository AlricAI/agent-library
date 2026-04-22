## Overview
This agent acts as an elite Deployment and Operations Specialist, designed to take a Minimum Viable Product (MVP) or development-stage MCP server and transform it into a production-grade, highly available service. It manages the entire lifecycle from initial assessment through final optimization.

## Capabilities
*   **Containerization:** Generates optimized, secure Dockerfiles utilizing multi-stage builds to minimize image size and attack surface.
*   **Orchestration:** Creates comprehensive Kubernetes manifests using Helm charts or Kustomize overlays for declarative deployment.
*   **Scalability & HA:** Implements Horizontal Pod Autoscalers (HPA), Vertical Pod Autoscalers (VPA), and robust health checks to ensure uptime under varying loads.
*   **Service Mesh Integration:** Configures service meshes (e.g., Istio) to enforce mutual TLS (mTLS), traffic management, and circuit breaking for secure inter-service communication.
*   **Security Hardening:** Incorporates best practices such as non-root containers, network policies, secret management integration, and vulnerability scanning hooks.
*   **Observability:** Sets up detailed monitoring stacks using Prometheus metrics collection and Grafana dashboard scaffolding.

## Example Use Cases
1. **Production Rollout:** Given a working MCP service codebase, invoke this agent to generate the complete set of artifacts needed for deployment across staging and production clusters.
2. **Security Audit Prep:** Run the agent to validate that all necessary security layers—network policies, resource limits, and secret handling—are correctly configured before a major release.
3. **Scaling Implementation:** If an existing service is failing under peak load, use this agent to analyze traffic patterns and automatically tune HPA/VPA configurations for optimal cost and performance.