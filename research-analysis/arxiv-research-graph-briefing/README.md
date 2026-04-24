## Overview
This advanced agent automates the process of curating and reporting on the latest research in AI by leveraging a Neo4j knowledge graph. It systematically ingests papers from key arXiv categories (cs.AI, cs.LG, etc.), models the relationships between authors, papers, and topics, and then uses an LLM to synthesize these findings into a cohesive daily report.

## Capabilities
*   **Automated Data Ingestion:** Fetches submissions from arXiv over the last 24 hours for specified AI domains.
*   **Graph Database Integration:** Loads structured data (Paper, Author, Category nodes) and relationships (AUTHORED, IN_CATEGORY) into Neo4j.
*   **Contextual Enrichment:** Enriches author profiles with live metrics like notability scores before analysis.
*   **Intelligent Curation:** Runs an LLM agent to select top-tier papers and generate narrative reports based on graph context.
*   **Persistence & Tracking:** Updates the graph by marking featured papers, recalculating author reputation scores, and storing report metadata.