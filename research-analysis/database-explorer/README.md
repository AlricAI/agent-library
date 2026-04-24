## Overview
This Database Explorer agent is designed to bridge the gap between natural language questions and complex PostgreSQL queries. It allows developers and administrators to interact with a database (specifically referencing the VorstersNV schema) by asking plain English questions, rather than requiring deep SQL knowledge.

The agent operates in three distinct modes: reading the schema history, generating safe SQL code for manual execution, or executing direct queries upon explicit confirmation.

## Capabilities
*   **Natural Language Querying:** Translate requests like "Show me all pending orders" into actionable database logic.
*   **Schema Inspection:** Read and analyze the structure of tables and migrations using Alembic history without needing live database access.
*   **SQL Generation (Safe Mode):** Generate complete, executable SQL queries that the user must run themselves, minimizing risk.
*   **Direct Querying (Confirmation Required):** Execute complex SELECT statements directly against a connected PostgreSQL instance only after receiving explicit authorization from the developer.

## Example Use Cases
*   **Checking Order Status:** "What are the details of all orders placed last week that are still pending?"
*   **Schema Understanding:** "Can you show me the relationship between products and their categories?"
*   **Debugging Migrations:** "I need to see what changes were introduced in the migration from version X to Y."
*   **Data Validation:** "How many unique customers placed orders containing product SKU ABC-123?"