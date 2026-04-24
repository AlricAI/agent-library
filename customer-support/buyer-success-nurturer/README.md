## Overview
This agent is designed to act as a sophisticated, lightweight Customer Success Manager (CSM) focused on the crucial period *after* initial product deployment. Its primary goal is not aggressive upselling, but rather maintaining deep visibility into buyer adoption and integration health using event-driven signals.

It moves beyond simple ticket tracking by analyzing usage patterns to distinguish between quiet satisfaction and genuine disengagement, ensuring that outreach is timely, relevant, and non-intrusive.

## Capabilities
*   **Adoption Signal Detection:** Monitors actual product usage against purchased/accessed features to flag declining engagement immediately.
*   **Health Check Analysis:** Assesses the technical integration health by reviewing session logs and site-world loading success rates.
*   **Nuanced Communication Strategy:** Determines the optimal timing for outreach—knowing when to prompt action versus when to allow users space to work.
*   **Signal Triage:** Categorizes incoming feedback into actionable buckets: Product Friction (needs development), Edge Case (requires support), or Expansion Opportunity (suggests next phase).
*   **Risk Scoring:** Provides a risk assessment score for each buyer, flagging immediate churn risks versus those who are simply in a slower adoption cycle.

## Example Use Cases
*   **Proactive Intervention:** A key client's usage drops by 40% week-over-week. The agent flags this, investigates if it’s an integration failure (Blueprint issue) or process change (Client issue), and recommends a targeted check-in.
*   **Opportunity Identification:** Usage data shows a buyer frequently accessing the 'Inventory Management' module but never touching the 'Supplier Portal.' The agent suggests scheduling a demo focused specifically on connecting those two workflows, framing it as an efficiency improvement rather than an upsell.
*   **Feedback Loop Management:** A buyer reports a minor UI glitch. The agent logs this immediately, routes it to the correct engineering queue, and sets a follow-up task to confirm resolution, ensuring no reported issue is ever dropped.