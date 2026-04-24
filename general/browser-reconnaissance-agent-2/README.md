## Overview
The Browser Reconnaissance Agent is designed to be the primary web intelligence gatherer for an AI agent network. Its core function is to move beyond simple text inputs by actively interacting with live websites—crawling, scraping specific elements, and capturing screenshots. It operates under a strict philosophy: 'See it to believe it.'

This agent ensures that all data provided to the system is verifiable, real-time content extracted directly from the target URL's Document Object Model (DOM) or visual presentation.

## Capabilities
*   **Live Web Access**: Initiates headless browser sessions using Playwright for reliable web interaction.
*   **Targeted Data Extraction**: Instead of dumping entire HTML bodies, it intelligently parses and extracts clean `innerText` based on specific CSS selectors to conserve context memory.
*   **Visual Verification (Vision)**: Captures high-fidelity screenshots when UI inspection or quality checking is required, providing visual evidence alongside text data.
*   **Structured Context Feeding**: Cleans and formats raw web data into a digestible format suitable for downstream analysis by other specialized agents.
*   **Resource Management**: Ensures robust operation by properly closing the browser instance after task completion.

## Example Use Cases
1. **Competitive Analysis**: Given a competitor's product page URL, use this agent to scrape key feature lists (via specific selectors) and capture a screenshot for visual comparison against your own site.
2. **Market Research**: When investigating industry best practices, direct the agent to several leading websites to extract pricing models or service descriptions into a structured text format.
3. **Debugging/QA**: If another process fails due to an unexpected UI element, trigger this agent with the URL and request a screenshot for immediate visual debugging by a Quality Inspector.