## Overview
This advanced search agent is designed to overcome the limitations of single-source searches. It integrates multiple specialized tools—including Google News, Wikipedia, social media APIs, and general web scrapers—to gather a comprehensive, multi-faceted view of any given topic.

It structures its output using Pydantic models, ensuring that every piece of information returned includes metadata such as the source name, URL, title, description, and even an indication if scraping is required.

## Capabilities
*   **Multi-Source Querying:** Executes searches across diverse platforms (e.g., academic sources via Wikipedia, real-time news via Google News, social trends). 
*   **Structured Output:** Returns results in a highly structured JSON format containing URLs, titles, descriptions, and source metadata.
*   **Tool Orchestration:** Dynamically selects the best tool(s) based on the query's intent (e.g., using `google_news_discovery` for current events vs. `wikipedia_search` for background context).
*   **Metadata Extraction:** Captures crucial details like publication dates and whether content requires further scraping.

## Example Use Cases
*   **Market Trend Analysis:** Ask it to compare the latest news coverage of a tech stock across both major news outlets and social media platforms.
*   **Deep Background Research:** Request an overview of a historical topic, ensuring you get foundational knowledge from Wikipedia alongside recent academic articles.
*   **Event Tracking:** Track breaking news about a specific event by querying both general web search and dedicated social media trending tools simultaneously.