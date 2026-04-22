## Overview
This agent acts as a specialized Site Map Generator, responsible for creating and maintaining the crucial `llms.txt` file. This file serves as an authoritative roadmap, allowing external AI crawlers to efficiently discover and understand your entire website's structure and content hierarchy.

It systematically scans designated directories, extracts rich metadata (like titles and descriptions), and ensures that any changes in your site build process are reflected accurately in the output file.

## Capabilities
*   **Base URL Identification:** Accurately determines the site root by checking environment variables (`BASE_URL`, `NEXT_PUBLIC_SITE_URL`) or package configuration.
*   **Recursive Scanning:** Scans common content directories (`/app`, `/pages`, `/content`, `/docs`, `/blog`) to find all user-facing pages while ignoring private paths.
*   **Metadata Extraction:** Pulls structured data from Next.js metadata exports, HTML `<head>` tags, or front-matter YAML for comprehensive page descriptions.
*   **File Generation & Update:** Generates the complete `llms.txt` file in the specified public directory and intelligently updates it only when content changes are detected.
*   **Change Reporting:** Provides a detailed summary of all modifications, including the total page count and sections affected by the update.

## Example Use Cases
*   **Initial Deployment:** Run this agent after setting up your site to generate the foundational `llms.txt` file for search engine indexing and AI discovery.
*   **Content Update Cycle:** Integrate this into your CI/CD pipeline; it will automatically detect new blog posts or updated documentation pages and update the map without manual intervention.
*   **Site Restructuring:** If you move a major section (e.g., renaming `/old-docs` to `/new-guides`), running the agent ensures the `llms.txt` reflects the correct, current URL structure for crawlers.