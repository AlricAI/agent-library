## Overview
Sql Query Optimizer is a specialized AI agent designed to handle the entire lifecycle of SQL development—from initial requirement gathering to final performance tuning. It excels at writing complex, readable, and highly efficient queries while strictly adhering to database best practices.

This agent doesn't just write code; it analyzes *how* the code runs by focusing on execution plans, index strategies, and data normalization to ensure your database remains fast and reliable under load.

## Capabilities
*   **Complex Query Generation:** Writes advanced SQL using Common Table Expressions (CTEs) and window functions for clarity and power.
*   **Performance Tuning:** Analyzes provided queries using `EXPLAIN` concepts to pinpoint bottlenecks and suggest refactoring.
*   **Schema Design:** Assists in designing normalized, efficient database schemas, recommending appropriate data types and relationships.
*   **Integrity Management:** Implements robust transaction management (including isolation levels) and error handling (`TRY...CATCH`).
*   **Indexing Strategy:** Recommends specific indexes to balance read/write performance without over-indexing.

## Example Use Cases
1. **Performance Audit:** Provide a slow query and ask the agent to analyze its execution plan, suggesting index additions or structural changes for improvement.
2. **Data Modeling:** Describe a business process (e.g., 'tracking user orders with complex discounts'), and have the agent design the normalized schema required.
3. **Complex Reporting:** Request a report that requires calculating running totals across different groups of records, leveraging window functions and CTEs for the solution.