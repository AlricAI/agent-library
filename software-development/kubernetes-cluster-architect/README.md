## Overview
This agent embodies the knowledge of a senior Kubernetes specialist, focusing on building and maintaining highly reliable, enterprise-grade container orchestration platforms. It guides users through every aspect of cluster lifecycle management, from initial architecture design to advanced security hardening.

## Capabilities
*   **Cluster Design:** Advises on control plane setup, etcd configuration, multi-master topologies, and optimal node pool strategies for high availability.
*   **Workload Orchestration:** Implements best practices for Deployments, StatefulSets, Jobs, and advanced patterns like sidecars and init containers.
*   **Security Hardening:** Verifies compliance against benchmarks (e.g., CIS) and enforces granular security policies using RBAC and Network Policies.
*   **Resource Optimization:** Manages resource allocation via Quotas, LimitRanges, HPA/VPA, ensuring optimal utilization while maintaining performance budgets.
*   **Networking & Storage:** Selects appropriate CNI solutions, configures Ingress controllers, and manages persistent storage through CSI drivers and dynamic provisioning.

## Example Use Cases
*   **Designing a Multi-Tenant Cluster:** Need to deploy a cluster supporting multiple isolated teams? This agent will guide you on implementing namespace isolation, strict RBAC policies, and network segmentation using NetworkPolicies.
*   **Performance Tuning:** Your application pods are slow to start or resource utilization is erratic. Use this agent to analyze performance metrics and suggest optimizations for Pod startup times, HPA tuning, or better resource requests/limits.
*   **Disaster Recovery Planning:** Before a major rollout, you need assurance of uptime. This agent will help structure your disaster recovery plan by reviewing etcd backup strategies, multi-region deployment patterns, and upgrade procedures to ensure 99.95% uptime targets are met.