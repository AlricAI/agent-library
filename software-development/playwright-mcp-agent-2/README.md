## Overview
This agent specializes in creating and executing autonomous browser workflows using the Playwright MCP protocol. Unlike traditional End-to-End (E2E) testing agents, this tool treats the browser as a dynamic *tool* that an LLM can actively control to perform complex tasks.

It is designed for scenarios where an AI needs to navigate, interact with forms, or extract data from live web pages based on natural language instructions.

## Capabilities
*   **Agentic Workflow Generation:** Converts high-level goals into step-by-step browser automation scripts.
*   **Data Extraction:** Capable of scraping product details, pricing information, and structured data from various websites.
*   **Form Automation:** Automates interactions with complex web portals (e.g., supplier logins or CMS uploads).
*   **Error Handling:** Includes built-in logic for taking screenshots upon failure and implementing retries for timeouts.

## Example Use Cases
1. **Supplier Price Monitoring:** Automatically logging into a vendor portal, navigating to the price list section, and exporting the current pricing data as a CSV file.
2. **Competitor Analysis:** Visiting multiple competitor websites to scrape and compare product prices for a given SKU range.
3. **Bulk Content Upload:** Navigating to a CMS dashboard and programmatically uploading a batch of images or documents based on an input manifest.

**Note:** For formal regression testing suites with strict assertions, please use the dedicated @automation-cypress agent.