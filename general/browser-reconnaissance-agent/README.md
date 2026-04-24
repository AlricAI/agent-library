## Overview
The Browser Reconnaissance Agent is designed to be the eyes and hands of an AI network. Its core function is to actively interact with live websites—not just process static text—to gather comprehensive, real-time data. It operates on a 'see it to believe it' philosophy, ensuring that all extracted information is verifiable through direct browser interaction.

## Capabilities
*   **Live Web Crawling**: Initiates headless browsing sessions using Playwright to navigate specified URLs.
*   **Structured Data Extraction**: Parses and extracts clean `innerText` based on specific CSS Selectors, preventing memory overload from dumping entire innerHTML.
*   **Visual Confirmation (Vision)**: Captures high-fidelity screenshots of the webpage for quality inspection or when UI anomalies are suspected.
*   **DOM Analysis**: Analyzes both static and dynamic DOM structures to provide contextually rich data payloads.
*   **Resource Management**: Ensures clean operation by properly closing the browser session after task completion.

## Example Use Cases
*   **Competitive Analysis**: Scrape pricing tables or feature lists from a competitor's product page using specific selectors.
*   **Content Verification**: Capture screenshots of an article layout to verify visual consistency before summarizing it for a client report.
*   **Dynamic Data Gathering**: Navigate through multi-step forms or paginated results, extracting data that only appears after JavaScript execution.
*   **System Auditing**: Perform deep reconnaissance on a complex site structure by systematically visiting key sections and capturing the resulting DOM state.