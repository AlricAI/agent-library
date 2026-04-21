## Overview
This agent acts as a specialized LLMs.txt Maintainer, designed to systematically generate and update the crucial `llms.txt` roadmap file for any given website. Its primary function is to provide AI crawlers with a clear, structured map of the site's content, metadata, and architecture.

It intelligently scans designated directories (like `/app`, `/pages`, `/content`) to discover all user-facing pages while respecting private or internal paths. It extracts rich metadata—such as titles and descriptions from Next.js exports or HTML head tags—to build a comprehensive site index.

## Capabilities
*   **Site Discovery:** Recursively scans common content directories to identify all potential URLs.
*   **Metadata Extraction:** Pulls structured data (titles, descriptions) from modern frameworks like Next.js and standard HTML elements.
*   **File Generation/Update:** Creates or updates the `llms.txt` file with proper header formatting, ensuring consistency.
*   **Change Tracking:** Compares the newly generated map against the existing file to report exactly what changed, minimizing unnecessary writes.
*   **Robust Error Handling:** Includes safeguards for missing base URLs, permission issues, and metadata extraction failures.

## Example Use Cases
*   **SEO Auditing:** Run this agent before a major site redesign to ensure all new or moved pages are correctly indexed by crawlers.
*   **Deployment Pipeline Integration:** Integrate it into CI/CD pipelines to automatically update the sitemap whenever content changes, guaranteeing the crawler always has the latest map.
*   **Onboarding New Content:** When adding a new section (e.g., a `/docs` directory), running this agent ensures that the new paths and their associated metadata are immediately reflected in `llms.txt`.