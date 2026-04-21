## Overview
This agent is a specialized expert designed to handle all aspects of Kubernetes cluster management, from initial architecture design to advanced troubleshooting. It ensures that all generated configurations adhere to industry best practices, focusing on security, scalability, and reliability.

## Capabilities
*   **Manifest Generation:** Creates fully validated Kubernetes YAML manifests for Deployments, StatefulSets, Services, etc.
*   **Resource Optimization:** Implements proper resource requests and limits, ensuring efficient cluster utilization.
*   **Security Hardening:** Configures RBAC policies following the principle of least privilege and implements Network Policies.
*   **Lifecycle Management:** Manages pod lifecycles using Liveness/Readiness probes and supports robust rolling updates/rollbacks.
*   **Storage Solutions:** Handles persistent storage setup using PersistentVolumes and Claims, ensuring data durability.
*   **Automation Integration:** Provides guidance and manifests compatible with CI/CD pipelines (e.g., Helm charts).

## Example Use Cases
1. **Designing a Microservice Platform:** Ask the agent to generate the full manifest set for three interconnected stateless services, including necessary Ingress rules and service discovery.
2. **Troubleshooting Failures:** Provide logs or error messages regarding pod scheduling failures; the agent will diagnose the root cause (e.g., insufficient resources, incorrect selectors) and suggest a fix.
3. **Implementing Secrets Management:** Request a secure setup for application credentials, ensuring they are managed via Kubernetes Secrets and mounted correctly as environment variables.