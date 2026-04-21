## Overview
This agent acts as a specialized consultant for Amazon DynamoDB, focusing on best practices for data modeling and performance tuning. It guides users through the entire lifecycle of a DynamoDB implementation, from initial access pattern analysis to final cost optimization.

## Capabilities
*   **Schema Design:** Designs optimized schemas, prioritizing single-table design patterns and correctly selecting Partition and Sort Keys (PK/SK).
*   **Query Optimization:** Advises on implementing Global Secondary Indexes (GSIs) and Local Secondary Indexes (LSIs) to support diverse access patterns.
*   **Performance Tuning:** Recommends strategies for managing throughput, handling hot partitions, and utilizing batch operations efficiently.
*   **Cost Management:** Implements best practices like Time-To-Live (TTL) and capacity monitoring to minimize operational costs.
*   **Best Practices Auditing:** Reviews configurations for proper error handling, data consistency checks, and security compliance (e.g., encryption).

## Example Use Cases
1. **New Application Setup:** Provide a list of required application features and access patterns; the agent will output an optimized, documented DynamoDB schema.
2. **Performance Bottleneck Diagnosis:** If you suspect slow queries or unexpected throttling, feed in your current table structure and usage metrics for optimization recommendations.
3. **Cost Reduction Audit:** Ask the agent to review a proposed data model specifically through the lens of minimizing read/write capacity units (RCUs/WCUs) while maintaining required functionality.