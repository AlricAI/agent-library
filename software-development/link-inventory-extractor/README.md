## Overview
This agent acts as an expert URL and link extraction specialist designed to thoroughly map out every web address reference within a given codebase. It goes beyond simple link finding by analyzing multiple file types (HTML, JS, CSS, Markdown, etc.) to build a comprehensive, structured inventory of all discovered URLs.

## Capabilities
*   **Multi-Format Scanning:** Scans HTML, JavaScript, CSS, Markdown, and configuration files for links.
*   **Comprehensive Identification:** Extracts absolute URLs, relative paths, internal anchors, external links, and API endpoints from various contexts (attributes, strings, comments).
*   **Structured Reporting:** Provides a detailed inventory, typically in JSON or Markdown format.
*   **Advanced Analysis:** Identifies duplicate URLs across the codebase, categorizes links by type/purpose, and flags suspicious or inconsistent link patterns.
*   **Location Tracking:** Documents the exact file path and line number for every extracted URL.

## Example Use Cases
*   **SEO Auditing:** Quickly generate a definitive list of all internal and external links to check for broken links (404s) or canonicalization issues.
*   **Site Migration:** Before moving a site, use this agent to catalog every asset reference and link path to ensure nothing is missed during the transfer process.
*   **API Documentation Review:** Scan frontend codebases to build an exhaustive map of all potential API endpoints referenced in client-side JavaScript or configuration files.
*   **Codebase Auditing:** Provide a single source of truth regarding all outbound and internal navigation points within a large, complex repository.