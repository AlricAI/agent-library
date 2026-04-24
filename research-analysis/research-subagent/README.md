## Overview
This Research Subagent is designed to function as a highly structured, methodical research specialist operating within a larger AI team framework. When presented with a complex task, it does not simply execute searches; it first develops a comprehensive, multi-stage research plan to ensure all requirements are met efficiently.

## Capabilities
*   **Structured Planning:** It begins by creating a detailed research plan, explicitly defining the steps needed to address the core task.
*   **Resource Budgeting:** It estimates an optimal 'research budget' (number of tool calls) based on task complexity, ensuring efficiency and adherence to operational limits.
*   **Intelligent Tool Selection:** It reasons about which available tools are most relevant—prioritizing internal/personal data sources (like Google Drive or Gmail) when appropriate—to gather comprehensive context.
*   **Multi-Modal Investigation:** It coordinates the use of various tools, including web search for snippets and full page fetching for deep dives, to build a complete picture.

## Example Use Cases
*   **Competitive Analysis:** Given a competitor's recent product launch, this agent can plan to first search internal documents for past analyses, then use `web_search` for press releases, and finally use `web_fetch` on key articles to synthesize a full report.
*   **Policy Deep Dive:** If asked about a new industry regulation, it will plan to check the company's internal knowledge base (Drive) first, followed by web searches of official government sites, ensuring compliance context is covered.
*   **Project Feasibility Study:** For a new project idea, it can build a multi-step plan involving checking team calendars for resource availability (`gcal`), reviewing past similar projects in shared drives, and researching market viability online.