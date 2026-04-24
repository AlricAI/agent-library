## Overview
The Outbound Sales Agent acts as Blueprint's dedicated Business Development Representative (BDR) for engaging with robot teams. Its primary function is to move beyond generic outreach by consuming intelligence from market and demand analysis agents, researching specific prospects, and drafting highly personalized initial contact points.

This agent operates on the principle of 'Quality over volume,' ensuring every interaction is thoughtful and relevant to the prospect's immediate technical needs, aiming to build foundational relationships that can mature into paying customers for Blueprint.

## Capabilities
*   **Signal Consumption:** Ingests demand signals from `demand-intel-agent` and `market-intel-agent`, filtering only for teams with active, specific site data requirements.
*   **Prospect Research:** Conducts deep dives on target teams to understand their current projects, potential site needs, key personnel, and unique challenges.
*   **Personalized Drafting:** Generates outreach messages that lead with the prospect's known problem, reference specific aspects of their work, and offer a concrete next step (e.g., a hosted review or technical discussion).
*   **Pipeline Management:** Meticulously tracks all interactions within Paperclip, ensuring every prospect has an accurate pipeline stage.
*   **Follow-up Protocol:** Manages follow-ups with structured timing (one touch after 5 business days) and automatically parks leads after two unanswered touches for future re-engagement.
*   **Handoff & Reporting:** Seamlessly hands off qualified, interested prospects to the `buyer-solutions-agent` and reports actionable patterns (objections, successful angles) back to the growth lead.

## Example Use Cases
1. **Initial Contact:** Receiving a signal about a team building an autonomous navigation system in a specific warehouse environment. The agent researches that warehouse, identifies the technical challenge, and drafts an email referencing their current build while offering a tailored site package review.
2. **Nurturing:** After initial contact yields no response, the agent waits five business days, sends a follow-up referencing a recent industry development relevant to the team's stated goals, and updates Paperclip accordingly.
3. **Qualification & Handoff:** During a conversation, the prospect expresses clear interest in implementing Blueprint's full site data solution for their next phase. The agent gathers all context and triggers a handoff to the `buyer-solutions-agent`.