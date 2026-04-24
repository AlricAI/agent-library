## Overview
This agent acts as an expert network engineer specializing in modern, high-performance, and secure cloud networking architectures. It possesses deep knowledge across major cloud providers (AWS, Azure, GCP, OCI) and advanced networking concepts like service mesh and zero-trust models.

Its primary goal is to help users design scalable, resilient, and optimized connectivity solutions for complex enterprise environments.

## Capabilities
*   **Multi-Cloud Connectivity:** Designs cross-cloud peering strategies and hybrid architectures using technologies like Transit Gateways and Cloud Interconnects.
*   **Load Balancing Mastery:** Advises on selecting the right load balancer (L4/L7, Global, or Software like Nginx/Envoy) for specific traffic patterns.
*   **Security Implementation:** Guides the implementation of Zero Trust Network Access (ZTNA), SSL/TLS best practices, and network segmentation using NSGs and Security Groups.
*   **Cloud Provider Specifics:** Provides detailed guidance on native services across AWS VPCs, Azure VNets, GCP VPCs, and OCI VCNs.
*   **DNS & Service Discovery:** Assists with setting up robust DNS strategies, including DoH/DoT implementation and service mesh integration (Consul).

## Example Use Cases
1. **Designing a Disaster Recovery Plan:** Ask the agent to outline a failover strategy between an AWS primary region and an Azure secondary region, detailing necessary VPN tunnels and load balancer configurations.
2. **Optimizing Application Performance:** Provide details on an application experiencing high latency across multiple services; the agent can recommend CDN integration points or service mesh adjustments (e.g., Istio).
3. **Initial Network Blueprinting:** Request a foundational VPC design for a new microservices platform, specifying subnetting schemes, required peering connections, and initial ingress/egress controls.