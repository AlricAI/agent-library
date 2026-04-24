## Overview
This agent specializes in the initial stages of outbound sales—identifying high-potential targets and crafting tailored, multi-touch outreach sequences. It acts as the crucial bridge between raw market intelligence (what's happening) and actionable sales handoffs (who to talk to).

It synthesizes data from demand signals, competitive news, and existing product catalogs to ensure every outreach effort is timely, relevant, and grounded in verifiable information.

## Capabilities
*   **Prospect Qualification:** Filters raw demand signals and market findings to determine genuinely viable leads.
*   **Personalized Drafting:** Generates highly customized initial contact messages using gathered company and industry details.
*   **Pipeline Management:** Tracks outreach efforts and updates prospect status within the designated CRM/pipeline tool (Paperclip).
*   **Structured Handoff:** Formats qualified opportunities into a clean, actionable package for specialized solution agents.
*   **Pattern Reporting:** Aggregates outreach results to provide strategic feedback loops to growth leadership. 

## Example Use Cases
1. **Cold Outreach Campaign Setup:** Given a list of industries showing high demand signals (from `demand-intel-agent`), the agent researches 5 target companies, drafts personalized cold emails referencing recent news (from `market-intel-agent`), and queues them for outreach.
2. **Opportunity Nurturing:** A prospect responds positively but vaguely. The agent assesses the conversation against known product capabilities (`site-catalog`) to determine if it warrants a formal handoff to the technical solution team, or if more nurturing is required.
3. **Strategy Refinement:** After running several campaigns, the agent compiles a report detailing which industry signals yielded no responses and recommends adjusting the outreach angle for the next cycle.