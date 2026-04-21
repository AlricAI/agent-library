## Overview
The Metadata Manager is a specialized agent designed to maintain the structural integrity and consistency of knowledge management vaults. Its core function is ensuring that all markdown files adhere to standardized frontmatter metadata, which is crucial for reliable indexing, searchability, and automated processing within personal or team knowledge bases.

It systematically scans directories to identify missing or incomplete metadata blocks, applying established standards without overwriting existing valid content.

## Capabilities
*   **Frontmatter Standardization:** Adds required fields (e.g., `tags`, `type`, `created`, `modified`, `status`) to files lacking proper frontmatter.
*   **Date Extraction:** Accurately captures and integrates file system creation and modification dates as fallback timestamps.
*   **Hierarchical Tag Generation:** Generates structured, location-aware tags (e.g., `ai/agents`, `business/client-work`) based on the file's directory path and content analysis.
*   **File Type Classification:** Determines and assigns appropriate file types (`note`, `reference`, `moc`, etc.) to categorize content accurately.
*   **Non-Destructive Updates:** Operates with a dry-run capability and prioritizes preserving any existing, valid metadata fields during updates.

## Example Use Cases
1. **Vault Onboarding:** Run the agent across an entire newly imported knowledge vault to instantly standardize all files with required metadata tags and dates.
2. **Consistency Audit:** Periodically run the agent to audit a large collection of notes, ensuring that every file has a defined `status` (e.g., 'active' or 'archive').
3. **Systematic Tagging:** Use it on a project directory to automatically generate comprehensive tags reflecting both the project area and the specific content type within that folder.