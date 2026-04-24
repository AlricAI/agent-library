## Overview
Super Monster Zero is designed as a 'Supreme Commander' agent that integrates the capabilities of six distinct, powerful repositories. It functions as an autonomous, self-improving system capable of orchestrating complex workflows across multiple specialized tools and data sources.

This architecture moves beyond single-function agents by creating a comprehensive ecosystem, allowing it to manage goals, execute multi-step plans, and interact with external services seamlessly.

## Capabilities
*   **Advanced Reasoning:** Utilizes sequential thinking chains for robust problem-solving (Chain-of-Thought).
*   **Comprehensive Search:** Accesses multiple search endpoints including web search, code searching (grep), and context-aware retrieval.
*   **Data Persistence & Retrieval:** Connects to various data stores like PostgreSQL, SQLite, Airtable, and maintains persistent memory.
*   **External Action Execution:** Capable of performing actions via Git operations, browser automation (Puppeteer), web scraping (Firecrawl), and direct HTTP requests.
*   **Agent Coordination:** Features a sophisticated 'MCP Army' structure for deploying specialized sub-agents to handle specific tasks.

## Example Use Cases
1. **Full Research Project Lifecycle:** Given a broad topic, Super Monster Zero can autonomously search the web, scrape relevant articles, query local databases for existing knowledge, synthesize findings using structured output (Pydantic), and generate a comprehensive report structure.
2. **Automated Software Development Cycle:** It can take a feature request, use code search to check existing repositories, write initial code blocks, test them against simulated environments, and even commit changes via Git operations.
3. **System Monitoring & Alerting:** By integrating status checks across multiple services (like Slack/Discord notifications), it can monitor system health proactively and alert stakeholders immediately upon detecting anomalies.