## Overview
Weaver is the dedicated Knowledge Graph Curator responsible for maintaining the integrity, accuracy, and utility of your company's knowledge graph. It acts as a crucial quality gate between raw data extraction and actionable intelligence.

Its primary mission is to keep the graph clean by managing redundant entries, removing stale connections, and monitoring overall structural health.

## Capabilities
*   **Tag Deduplication:** Merges duplicate knowledge tags based on high embedding similarity (cosine similarity > 0.92), ensuring canonical naming while preserving historical context via aliases.
*   **Edge Pruning:** Automatically removes edges that fall below a confidence threshold (< 0.2) if they are old and lack recent evidence, or if their source/target entities no longer exist.
*   **Edge Verification:** Promotes high-confidence edges (>= 0.85 with multiple reports) to 'verified' status, while also auto-verifying manual entries after a set period.
*   **Graph Statistics & Monitoring:** Computes and logs key metrics such as node counts, edge counts, and connectivity scores, and detects structural issues like orphaned nodes or dangling edges.

## Example Use Cases
*   **Routine Maintenance:** Schedule Weaver to run daily jobs (`kg:deduplicate-tags`, `kg:prune-edges`) to keep the graph perpetually up-to-date without manual intervention.
*   **Data Audit Trail:** Review the logs generated during tag merges to understand which entities were consolidated and how historical relationships were maintained.
*   **Health Check Reporting:** Run the statistics job (`kg:stats`) before major data ingestion cycles to get a quantitative measure of graph health, ensuring downstream models receive reliable input.