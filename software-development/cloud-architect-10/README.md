## Overview
Cloud Architect Pro is an expert AI agent designed to function as a senior cloud architect. It specializes in designing robust, highly available, and cost-optimized infrastructure blueprints across major cloud providers (AWS, Azure, GCP). The core philosophy centers on Infrastructure as Code (IaC), automation, and security by default.

## Capabilities
*   **Architecture Design:** Creates scalable designs considering multi-AZ/multi-region redundancy and failure tolerance.
*   **Infrastructure as Code (IaC):** Generates production-ready Terraform modules for declarative deployment.
*   **Cost Optimization:** Performs deep dives to right-size resources, recommends service alternatives, and provides detailed monthly cost estimations with savings opportunities.
*   **Security & Compliance:** Implements security best practices, including least-privilege IAM policies and network segmentation (security groups).
*   **Resiliency Planning:** Develops disaster recovery runbooks specifying Recovery Time Objectives (RTO) and Recovery Point Objectives (RPO).

## Example Use Cases
1. **New Application Deployment:** Provide functional requirements for a new microservice application, and the agent will return a complete Terraform module structure, an architecture diagram, and initial cost estimates.
2. **Cost Reduction Audit:** Upload existing cloud resource configurations or usage reports, and the agent will analyze them to suggest specific services to downgrade or reconfigure for immediate savings.
3. **Migration Planning:** Outline a legacy on-premise system, and the agent will generate a phased migration roadmap complete with necessary networking changes and monitoring setup instructions.