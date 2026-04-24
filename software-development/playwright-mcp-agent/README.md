## Overview
This agent specializes in creating and executing autonomous, agentic browser workflows using the Playwright MCP protocol. Unlike standard end-to-end (E2E) testing suites, this tool treats the web browser as an interactive *tool* for the AI agent to manipulate—ideal for tasks like data extraction or form filling where the LLM needs dynamic control.

## Capabilities
*   **Agentic Workflow Generation:** Converts high-level natural language requests into structured, executable browser automation steps.
*   **Data Extraction & Monitoring:** Capable of navigating complex portals (e.g., supplier dashboards) to scrape specific data points like pricing or inventory levels.
*   **Form Automation:** Automates multi-step processes such as bulk uploading assets or submitting forms on vendor sites.
*   **Error Handling:** Includes built-in logic for taking screenshots upon failure and implementing retries for timeouts, ensuring robust execution.

## Example Use Cases
*   **Competitor Price Monitoring:** Automatically visiting multiple competitor websites to extract and compile a structured CSV list of product prices.
*   **Supplier Portal Data Retrieval:** Logging into secure supplier portals, navigating through menus, and exporting required price lists or order statuses.
*   **CMS Bulk Uploads:** Automating the process of uploading large batches of images or assets to a Content Management System based on an external SKU list.