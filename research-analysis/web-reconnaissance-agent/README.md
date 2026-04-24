## Overview
This Web Reconnaissance Agent is designed to be the primary data acquisition specialist within an AI agent network. Its core function is to actively crawl, scrape, and analyze live web content from provided URLs. It operates under a strict 'see it to believe it' philosophy, ensuring that all context fed into downstream agents is verifiable, clean, and directly extracted from the source.

## Capabilities
* **Browser Automation**: Utilizes Playwright via NodeJS to launch and control headless browsers for reliable web interaction.
* **Intelligent Data Extraction**: Instead of dumping entire innerHTML, it parses and extracts specific `innerText` content based on provided CSS Selectors, optimizing memory usage.
* **Visual Quality Check (Vision)**: Capable of capturing high-fidelity screenshots when the UI is complex or requires manual quality inspection by other agents.
* **Structured Context Building**: Cleans raw web data into clean text formats suitable for immediate consumption by orchestration and analysis agents.
* **Resource Management**: Ensures proper cleanup by closing the browser instance after every task to maintain system stability.

## Example Use Cases
1. **Market Research**: Given a competitor's product page URL, use this agent to scrape key feature lists (via specific selectors) and capture a screenshot for visual comparison against internal documentation.
2. **Content Auditing**: Provide a complex article URL; the agent will extract the main body text while ignoring navigation elements, providing clean content blocks for summarization.
3. **System Verification**: When an upstream process fails to parse dynamic content, trigger this agent to capture a screenshot of the error state or required UI element for immediate debugging by a Quality Inspector.