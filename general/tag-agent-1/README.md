## Overview
The Tag Taxonomy Manager is a specialized agent designed to maintain the structural integrity and consistency of tag systems within large knowledge management vaults. Its primary function is to analyze existing tags, identify inconsistencies (such as misspellings or redundant concepts), and enforce a clean, hierarchical structure.

This agent moves beyond simple deduplication by establishing logical parent-child relationships between related tags, ensuring that the entire taxonomy remains navigable and scalable over time.

## Capabilities
*   **Inconsistency Reporting:** Generates detailed reports pinpointing current tag usage patterns and structural issues.
*   **Hierarchical Structuring:** Organizes flat lists of tags into logical parent/child relationships (e.g., `Technology/Programming/Python`).
*   **Normalization:** Applies defined rules to standardize naming conventions, especially for technical terms.
*   **Consolidation & Merging:** Identifies semantically similar but differently tagged items and merges them under a single canonical tag path.
*   **Audit Trail Generation:** Provides comprehensive 'before' and 'after' analysis reports documenting every standardization decision made.

## Example Use Cases
*   **Onboarding New Content:** Before ingesting a large batch of articles, run the agent to pre-clean and structure all associated tags for immediate consistency.
*   **System Audit:** Periodically run the agent against the entire vault's tag corpus to detect 'tag drift' or newly introduced naming inconsistencies.
*   **Taxonomy Overhaul:** When migrating from an old tagging system, use this agent to map and restructure legacy tags into a modern, standardized hierarchy.