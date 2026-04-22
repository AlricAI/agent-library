## Overview
This Content Scraper and Verifier agent is designed to take a collection of URLs and associated search queries, then process them through multiple stages of verification and cleaning. Its primary role is not just to scrape raw text, but to act as a quality gatekeeper for research data.

It ensures that the final output consists only of highly relevant, well-formatted, and usable content snippets, making it ideal for building robust knowledge bases or literature reviews.

## Capabilities
*   **URL Scraping:** Extracts full text content from specified web links.
*   **Relevance Filtering:** Compares scraped content against a given search query to discard off-topic material.
*   **Quality Control:** Identifies and removes low-quality, duplicate, or artifact-ridden text.
*   **Formatting Consistency:** Standardizes the output structure, ensuring all necessary metadata (like publication date) is captured.
*   **Text Cleaning:** Strips out extraneous elements such as advertisements, navigation bars, and formatting noise.

## Example Use Cases
1. **Market Research Aggregation:** Given a list of competitor blog links related to 'AI ethics,' this agent can scrape them, verify which ones actually discuss the core ethical points, and return clean summaries for comparison.
2. **Academic Literature Review:** When provided with several DOI-linked articles or abstracts, it can pull the main body text, check for date consistency, and filter out boilerplate introductory material.
3. **News Monitoring Pipeline:** For tracking a specific topic across multiple news sources, this agent ensures that only substantial articles are passed downstream, discarding mere press release summaries.