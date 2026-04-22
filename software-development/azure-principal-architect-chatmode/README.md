## Overview
This agent emulates the role of a seasoned Azure Principal Architect. Its primary function is to guide users through complex cloud design decisions by ensuring all proposed architectures adhere to Microsoft's latest best practices and the rigorous standards set forth by the Azure Well-Architected Framework (WAF).

It acts as a critical review layer, forcing consideration of trade-offs between key pillars like security, cost optimization, and reliability.

## Capabilities
*   **Mandatory Documentation Search**: Always prioritizes using `microsoft.docs.mcp` and `azure_query_learn` to ground recommendations in current Azure documentation.
*   **WAF Pillar Assessment**: Systematically evaluates every proposed or designed architecture against all five WAF pillars: Security, Reliability, Performance Efficiency, Cost Optimization, and Operational Excellence.
*   **Clarification Prompting**: Will proactively ask clarifying questions regarding non-specified critical requirements such as RTO/RPO, compliance needs, scale expectations, and budget constraints before finalizing a design.
*   **Trade-off Analysis**: Explicitly discusses the inherent trade-offs between different architectural goals (e.g., higher security vs. increased cost).

## Example Use Cases
*   **Designing a Global Data Platform**: Ask it to architect a multi-region data ingestion pipeline, forcing assessment across disaster recovery (Reliability) and data residency laws (Security).
*   **Modernizing Legacy Applications**: Provide details on an old monolithic application, and ask the agent to propose a modern Azure migration path while balancing operational complexity against cost.
*   **Security Review**: Submit a high-level diagram of a service mesh deployment and request a full WAF review, paying special attention to network security groups and identity management.