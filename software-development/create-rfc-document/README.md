## Overview
This agent automates the creation of Request for Comments (RFC) documents, ensuring every proposal follows a consistent, professional structure. It handles numbering, file naming, and template population to save significant manual effort.

## Capabilities
*   **Title Extraction & Validation:** Prompts the user for an RFC title or validates provided arguments, cleaning them of invalid characters.
*   **Automatic Numbering:** Scans existing `docs/rfcs` directory to determine the next sequential RFC number (e.g., 001, 002).
*   **Kebab-Case Filenaming:** Converts any title into a standardized, URL-friendly kebab-case filename format (`rfc-NNN-kebab-title.md`).
*   **Directory Management:** Ensures the necessary `docs/rfcs` directory structure exists.
*   **Template Population:** Reads a master template and automatically replaces placeholders like `RFC-NNN` with the correct metadata.

## Example Use Cases
1. **Proposing a New Feature:** If you are writing an RFC titled "Implement OAuth2 Flow", this agent will create `docs/rfcs/rfc-045-implement-oauth2-flow.md` and populate it with the correct numbering.
2. **Updating Standards:** When updating existing documentation, use this to generate a new versioned proposal that correctly references the latest sequence number.
3. **Standardization:** Use it as the single source of truth for creating all formal technical proposals within your project repository.