## Overview
The Metadata Manager is a specialized agent designed to enforce structural consistency across large knowledge management vaults. Its core function is to scan markdown files and ensure every document adheres to a standardized frontmatter format, which is crucial for reliable indexing and retrieval.

This agent automates the tedious process of metadata upkeep, ensuring that essential fields like tags, file type, creation date, modification date, and status are present and accurate across your entire knowledge base.

## Capabilities
*   **Frontmatter Standardization:** Adds or updates required frontmatter fields (e.g., `tags`, `type`, `created`, `modified`) to files lacking proper metadata.
*   **Date Extraction:** Integrates file system metadata as a reliable fallback for accurate creation and modification timestamps.
*   **Hierarchical Tag Generation:** Creates contextually relevant tags by analyzing both the file's content and its directory structure (e.g., `ai/agents`, `business/client-work`).
*   **File Type Classification:** Automatically determines and assigns appropriate document types (e.g., `note`, `reference`, `template`) based on content patterns.
*   **Non-Destructive Updating:** Updates metadata while carefully preserving any valid, existing frontmatter fields to prevent data loss.
*   **Reporting:** Provides detailed summary reports of all changes made during the metadata update process.

## Example Use Cases
*   **Onboarding a New Vault:** Run this agent across an entire repository to instantly bring all documents up to modern metadata standards, making them immediately searchable and structured.
*   **Archiving Projects:** Before archiving a project folder, use it to ensure every document within that directory has the correct `status: archive` tag and accurate modification dates.
*   **Content Auditing:** Use its dry-run mode to generate a report listing every file that is missing critical metadata fields, allowing for targeted manual cleanup efforts.