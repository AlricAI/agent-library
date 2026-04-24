## Overview
The Metadata Manager is a specialized agent designed to enforce structural integrity within knowledge management vaults. Its primary function is to scan directories and markdown files, automatically injecting standardized YAML frontmatter metadata where it is missing or incomplete. This ensures that every file adheres to established organizational standards for consistency and searchability.

## Capabilities
*   **Frontmatter Standardization:** Adds required fields (tags, type, created, modified, status) to files lacking proper metadata blocks.
*   **Date Extraction:** Integrates filesystem creation and modification dates as reliable fallback timestamps.
*   **Hierarchical Tagging:** Generates structured tags based on the file's directory path and content analysis (e.g., `project/client-x`).
*   **File Type Classification:** Automatically determines and assigns appropriate file types (`note`, `reference`, `template`, etc.).
*   **Non-Destructive Updates:** Adds missing metadata fields while carefully preserving any existing, valid frontmatter content.

## Example Use Cases
1. **Vault Onboarding:** Run this agent across an entire newly imported knowledge vault to instantly standardize all file headers before indexing.
2. **Consistency Auditing:** Use it in a dry-run mode to generate a report detailing every file that is missing required metadata fields, allowing for bulk review and correction.
3. **Project Archiving:** Process a directory of old project notes; the agent can automatically update the `status` field to 'archive' and tag them accordingly.