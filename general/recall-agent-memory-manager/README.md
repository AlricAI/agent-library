## Overview
Recall acts as the central memory manager for all agents. Its primary mission is to maintain a clean, useful, and efficient knowledge store by handling the entire lifecycle of agent memories—from initial writing to eventual archival.

It ensures that valuable facts (stored as subject-predicate-object triples) are not lost due to temporal decay or data redundancy, making them available for accurate semantic retrieval across different operational sessions.

## Capabilities
*   **Memory Lifecycle Management:** Handles the process of writing new memories, recalling stored knowledge, embedding unindexed facts, compacting duplicates, and expiring stale entries.
*   **Data Cleaning & Compaction:** Implements a strategy to detect and merge near-duplicate memories (similarity > 0.95) within an agent's memory set, retaining the highest confidence version.
*   **Semantic Indexing:** Periodically embeds unembedded memories using advanced models like BGE-M3 to enable powerful semantic search capabilities.
*   **Knowledge Graph Promotion:** Identifies high-confidence relationship memories (e.g., 'uses', 'built_on') and promotes them into a structured `company_relationships` knowledge graph for enhanced querying.
*   **Usage Monitoring:** Monitors memory accumulation per agent, flagging any agent that begins to exceed acceptable memory thresholds.

## Example Use Cases
*   **Knowledge Persistence:** After an agent completes a complex task involving multiple steps, Recall ensures all key facts learned—such as 'Company X uses Technology Y'—are permanently stored and retrievable later.
*   **Data Hygiene:** If two different agents record nearly identical information about a product feature, Recall automatically merges them, preventing memory bloat and ensuring the most accurate single source of truth remains.
*   **Contextual Retrieval:** When an agent starts a new session, it queries Recall using natural language questions, which are then mapped to stored memories via semantic search for immediate context.
*   **Relationship Mapping:** If multiple agents confirm that 'Service A' is built on 'Framework B', Recall promotes this consensus into the core knowledge graph, making it discoverable by other systems.