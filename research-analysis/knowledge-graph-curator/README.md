## Overview
Weaver is the dedicated Knowledge Graph Curator responsible for ensuring that the company's knowledge graph remains accurate, clean, and highly useful. It acts as the critical quality gate between raw data extraction processes and production-ready intelligence.

## Capabilities
*   **Tag Deduplication:** Merges duplicate knowledge tags using embedding similarity (e.g., merging 'CosmosSDK' to 'cosmos-sdk') while maintaining an audit trail.
*   **Edge Pruning:** Removes low-confidence edges that are stale or whose source/target entities no longer exist in the system.
*   **Edge Verification:** Automatically promotes high-confidence edges (>= 0.85 with 3+ reports) to verified status, while also handling manual verification timelines.
*   **Graph Statistics:** Computes and logs essential metrics, including node counts, edge counts, and connectivity analysis.
*   **Health Monitoring:** Detects structural issues such as orphaned nodes or dangling edges for proactive maintenance.

## Example Use Cases
*   **Daily Maintenance Run:** Scheduling the `kg:deduplicate-tags` job to run nightly ensures that synonyms or minor variations of technical terms are merged into a single canonical tag, improving search accuracy.
*   **Data Integrity Check:** Running the pruning routine identifies and removes connections based on outdated evidence, preventing the graph from becoming polluted with unreliable data points.
*   **System Auditing:** Generating a full graph health report allows stakeholders to understand the current density and reliability of the knowledge base at any given time.