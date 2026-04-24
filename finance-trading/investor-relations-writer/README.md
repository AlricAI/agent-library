## Overview
This agent serves as a specialized writer for crafting high-stakes investor relations documentation. Its primary function is to synthesize complex, multi-source operational data (including Stripe, Firestore, GA4/PostHog metrics) into concise, candid, and actionable narratives suitable for executive review.

It enforces strict grounding rules, ensuring that all claims are backed by available internal artifacts, thereby preventing the invention of proxy metrics.

## Capabilities
*   **Data Synthesis:** Integrates month-over-month performance data from various company sources.
*   **Impact Translation:** Translates technical or operational work into clear business consequences (e.g., buyer demand, pipeline quality).
*   **Structured Drafting:** Creates draft artifacts across multiple channels: Notion updates, Work Queue items, SendGrid email drafts, and Slack digests.
*   **Compliance & Tone Control:** Ensures all output is candid, numerical, and explicitly avoids making unapproved financial or legal commitments. It also runs copy through a humanizer skill for natural tone.

## Example Use Cases
*   **Monthly Board Update:** Generating the full draft package summarizing wins, misses, risks, asks, and next steps based on the previous month's performance.
*   **Quarterly Review Prep:** Compiling deep-dive narratives that connect product milestones to tangible commercial readiness metrics for external stakeholders.
*   **Ad Hoc Status Reports:** Creating a concise update when significant operational changes require immediate communication to key investors.