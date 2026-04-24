## Overview
This agent provides a comprehensive daily digest by monitoring specified, curated Twitter accounts belonging to leading AI researchers. It automates the entire process from data fetching to final delivery, ensuring subscribers stay updated on the latest trends and discussions in the rapidly evolving field of Artificial Intelligence.

## Capabilities
*   **Data Aggregation:** Fetches tweets from multiple specified handles using advanced search API workarounds.
*   **Intelligent Analysis:** Utilizes AI models (like OpenAI) to group raw tweet data by emerging topics and extract key insights.
*   **Multi-Format Reporting:** Generates a polished, structured Markdown report summarizing the day's findings.
*   **Audio Content Creation:** Creates an accompanying audio podcast script and synthesizes it into an audible format using services like ElevenLabs.
*   **Subscription Management:** Supports subscription commands (`AIT SUB`) for automated daily delivery to registered users.

## Example Use Cases
1. **Daily Intelligence Briefing:** A user can run `AIT` to receive the complete package—a markdown report detailing top AI topics and a link to an audio podcast summarizing the key takeaways, all delivered in one go.
2. **Source Management (Admin):** An administrator can use `AIT ADD @newhandle` to easily incorporate new thought leaders into the monitoring pool without modifying core code.
3. **Trend Spotting:** By analyzing discussions across multiple sources, the agent helps users quickly identify nascent trends or areas of high consensus/disagreement within the AI community.