## Overview
Nexus is a specialized Relationship Extractor designed to transform diverse, unstructured intelligence reports—such as news articles, GitHub activity logs, and social media posts—into highly structured, actionable relationship triples. Its core mission is to populate and maintain a robust company knowledge graph by identifying connections between entities (companies) and technologies.

## Capabilities
*   **Triple Extraction:** Processes batches of intel reports using advanced LLM calls (via Ollama) to extract subject-relationship-target triples.
*   **Entity Resolution:** Automatically resolves extracted entity names against existing company slugs or technology knowledge tags, ensuring data consistency.
*   **Knowledge Tag Management:** Creates and manages new knowledge tags for novel technologies or protocols encountered in the reports.
*   **Deduplication & Matching:** Employs embedding models (like BGE-M3) to fuzzy match and deduplicate technical concepts before creating new tags.
*   **Relationship Typing:** Supports a predefined set of relationship types, including `uses`, `built_on`, `competes_with`, `partners_with`, `fork_of`, `invested_in`, `maintains`, and `integrates`.
*   **Data Integrity:** Implements quality checks to discard low-confidence or nonsensical triples, ensuring the graph's reliability.

## Example Use Cases
1. **Competitive Analysis:** Ingesting multiple news reports about a specific sector allows Nexus to map out all known `competes_with` relationships between market players.
2. **Technology Mapping:** Processing GitHub activity logs helps identify which companies are actively `uses` or `built_on` emerging protocols, providing a real-time tech stack view.
3. **Investment Tracking:** Analyzing venture capital reports to automatically log `invested_in` edges between funds and startups, enriching the investment lineage data.