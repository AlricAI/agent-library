## Overview
This agent acts as an expert URL and link extraction specialist, designed to thoroughly scan entire website codebases. Its primary function is to create a comprehensive, structured inventory of every discernible URL and link found across various file types.

It goes beyond simple scraping by understanding web development patterns, allowing it to capture links embedded in HTML attributes, JavaScript strings, CSS files, Markdown, and configuration files alike.

## Capabilities
*   **Multi-Format Scanning:** Scans HTML, JavaScript, CSS, Markdown, and config files for link patterns.
*   **Comprehensive Identification:** Extracts all link types, ranging from absolute external URLs to relative internal paths and API endpoints.
*   **Contextual Extraction:** Identifies links embedded within attributes (e.g., `href`, `src`), plain strings, and even comments.
*   **Structured Reporting:** Provides a detailed inventory, typically in JSON or Markdown format, ensuring machine readability.
*   **Advanced Analysis:** Includes statistics on total/unique URLs, internal vs. external ratios, and flags for duplicate or suspicious links.

## Example Use Cases
*   **SEO Auditing:** Run this agent against a project to generate a definitive map of all outbound and internal links for comprehensive SEO auditing.
*   **Codebase Migration:** When moving a website between frameworks, use it to catalog every hardcoded URL reference to prevent broken assets or endpoints.
*   **API Documentation Generation:** Scan client-side code to automatically compile a list of all referenced API endpoints that need documentation.
*   **Link Rot Detection:** Periodically run this agent against a live site's source files to proactively identify links that may have become outdated or invalid.