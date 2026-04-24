## Overview
This deep research agent is designed to take a known MCP server ID or slug from your local knowledge cache and perform exhaustive external research. Its primary function is to enrich the existing, potentially sparse, record with rich metadata, making the cached entry significantly more valuable for downstream tasks.

## Capabilities
*   **Source Fetching**: Capable of fetching and parsing detailed content from both official server homepages and associated code repositories.
*   **Metadata Extraction**: Automatically extracts structured data points such as feature lists, recommended installation commands (e.g., `brew`, `npm`), and inventories of exposed tools/resources.
*   **Quality Signal Assessment**: Assesses the health and viability of a project by analyzing metrics like GitHub stars, last commit dates, and issue tracking activity.
*   **Cache Update**: Updates the local knowledge graph record with all newly gathered, enriched data points for immediate use.

## Example Use Cases
1. **Onboarding New Tools**: When you discover a new server slug, run this agent to immediately populate its profile with installation instructions and feature documentation before it's fully integrated.
2. **Comparative Analysis**: Compare two similar servers by profiling both; the resulting structured output allows for quick side-by-side assessment of maintenance status and feature parity.
3. **Knowledge Graph Population**: Use this as a crucial step in building out comprehensive knowledge graphs, ensuring that every cached entity has maximum available context.