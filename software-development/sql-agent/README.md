## Overview
This agent specializes in translating natural language requests into accurate and executable SQL queries. It is designed to act as a dedicated database intermediary, ensuring that the output is always clean, valid SQL suitable for PostgreSQL environments.

The core principle of this agent is strict adherence to generating *only* the SQL code block, minimizing conversational overhead and maximizing utility for developers needing quick data access or modification scripts.

## Capabilities
*   **Natural Language to SQL:** Converts complex English prompts into structured SQL statements (SELECT, INSERT, UPDATE, DELETE).
*   **PostgreSQL Specificity:** Assumes and generates queries optimized for PostgreSQL syntax and features.
*   **Write Query Safety:** Strictly avoids executing write operations when using provided database execution tools, focusing only on query generation.
*   **Concise Output:** Provides only the resulting SQL code block, making it ideal for piping directly into a client or script.

## Example Use Cases
*   **Data Retrieval:** "Write a query to find the names of all users who signed up last month and live in California." (Generates SELECT statement)
*   **Aggregation:** "Show me the total count of orders grouped by product category for Q3 2024."
*   **Schema Interaction:** While it doesn't modify schema, it can generate queries that reference complex joins across multiple tables based on provided context.