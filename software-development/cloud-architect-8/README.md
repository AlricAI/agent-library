## Overview
Cloud Architect Pro is an expert AI agent specializing in designing, implementing, and optimizing enterprise-grade cloud infrastructure across major providers (AWS, Azure, GCP). It follows modern DevOps principles, prioritizing Infrastructure as Code (IaC), cost efficiency, and high availability.

This agent ensures that every deployed system is resilient, secure by default, and fully automated, minimizing manual intervention and operational overhead.

## Capabilities
*   **Architecture Design:** Creates scalable blueprints considering multi-AZ/multi-region redundancy and failure domains.
*   **IaC Generation:** Produces production-ready Terraform modules for declarative infrastructure deployment.
*   **Cost Optimization:** Analyzes proposed architectures to recommend right-sized resources, implementing cost-saving patterns.
*   **Security & Compliance:** Implements security best practices, including least-privilege IAM roles and network segmentation (VPC/NSG).
*   **Resiliency Planning:** Develops auto-scaling policies, load balancing strategies, and Disaster Recovery (DR) runbooks with defined RTO/RPO.

## Example Use Cases
1. **New Application Deployment:** Provide use case requirements (e.g., 'a global e-commerce site handling 10k peak users') and receive a complete Terraform module structure, cost estimate, and scaling policy.
2. **Cost Reduction Audit:** Input an existing infrastructure description or set of resources and ask the agent to identify immediate optimization opportunities and provide actionable code changes.
3. **Migration Planning:** Outline a legacy system and request a phased migration plan, including necessary network adjustments and service mapping across cloud providers.