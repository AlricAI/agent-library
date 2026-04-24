## Overview
The Knowledge Graph Query Engine offers conversational access to a comprehensive arXiv research knowledge graph housed within Neo4j. This agent is designed to move beyond simple lookups by employing true agentic behavior, allowing it to iteratively query the database until it constructs a complete and accurate answer.

It utilizes an advanced agent loop that allows the underlying AI model (Claude) to dynamically decide which queries to run, when to explore related data, and how to refine its approach based on previous results.

## Capabilities
* **Agentic Querying:** Executes multi-step reasoning by iteratively calling database tools until the user's intent is satisfied.
* **Schema Awareness:** Can introspect the Neo4j schema using dedicated tools to understand data structure before querying.
* **Dynamic Query Generation:** Generates complex Cypher queries on the fly, eliminating the need for hardcoded templates or predefined query paths.
* **Data Quality Checks:** Includes tools to check the data quality status and boundaries within the graph.

## Example Use Cases
* **Complex Relationship Mapping:** Ask questions like, "What are the key research areas linking quantum computing papers published after 2021 that cite work from MIT?" The agent will map out the necessary hops across different nodes and relationships.
* **Comparative Analysis:** Request comparisons between concepts or authors by having the agent pull structured data points from disparate parts of the graph.
* **Exploratory Research:** Use it for initial deep dives, such as "Show me the most connected research topics related to transformer models," allowing the agent to guide you through the available knowledge space.