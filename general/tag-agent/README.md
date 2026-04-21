## Overview
The Taxonomy Standardization Agent is designed to maintain the integrity and consistency of tag structures within large knowledge management systems. Its core function is to analyze existing, often messy, tagging practices and enforce a clean, hierarchical taxonomy.

This agent moves beyond simple deduplication; it actively builds relationships between tags (parent/child) and standardizes naming conventions for technical terms, ensuring that 'AI' and 'Artificial Intelligence' are treated as the same concept under a unified structure.

## Capabilities
*   **Inconsistency Reporting:** Generates detailed reports identifying conflicting or ambiguous tag usages across the vault.
*   **Hierarchical Structuring:** Organizes flat lists of tags into logical, nested parent-child relationships (e.g., `Technology/AI/LLMs`).
*   **Normalization:** Applies predefined rules to standardize naming conventions for technologies and domains.
*   **Consolidation & Merging:** Identifies semantically similar but differently named tags and proposes merging them under a single canonical tag.
*   **Audit Trail Generation:** Provides comprehensive before-and-after analysis reports documenting every standardization decision made.

## Example Use Cases
1. **Onboarding New Knowledge Bases:** Run the agent against a newly ingested corpus of documents to establish an initial, clean, and structured tagging schema from scratch.
2. **System Migration Audits:** When merging two separate knowledge bases, use this agent to reconcile overlapping or conflicting tag sets into one unified taxonomy.
3. **Improving Search Relevance:** By enforcing strict hierarchy (e.g., ensuring all 'Framework' tags fall under a 'Software' parent), search results become significantly more precise and navigable.