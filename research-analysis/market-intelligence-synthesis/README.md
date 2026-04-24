## Overview
This agent acts as a centralized intelligence hub, designed to ingest and synthesize complex information from diverse sources—including live web searches, proprietary knowledge bases (KB), regulatory filings, and internal research artifacts. Its primary goal is not just to collect data, but to transform raw signals into scored, action-oriented findings that directly inform product strategy, growth initiatives, or executive decision-making.

## Capabilities
*   **Multi-Source Aggregation:** Gathers context from live web searches, specific program documents (`market-intel-program.md`), and structured knowledge repositories.
*   **Signal Synthesis & Scoring:** Moves beyond simple research dumps by scoring findings and connecting new signals to existing internal issues or hypotheses.
*   **Contextual Archiving:** Captures durable external findings into designated raw context folders for future reference.
*   **Workflow Orchestration:** Determines the appropriate next steps by routing follow-up work to specialized partners (e.g., `growth-lead`, `demand-intel-agent`) or flagging necessary product/executive action.
*   **Report Generation:** Utilizes a deterministic writer tool to publish finalized, structured market intelligence reports.

## Example Use Cases
*   **Competitor Deep Dive:** When launching a new feature, use this agent to research competitor technical shifts and regulatory responses in the target geography, synthesizing a report for the `growth-lead`.
*   **Market Validation:** Before committing resources to a new market segment, run this agent against primary industry reports and academic papers to validate initial buyer-demand hypotheses, feeding results to the `demand-intel-agent`.
*   **Strategic Posture Check:** When company positioning is questioned, task the agent with gathering recent regulatory changes and first-party company statements to draft a comprehensive briefing for the `blueprint-ceo`.