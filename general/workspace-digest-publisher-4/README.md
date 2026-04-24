## Overview
This agent is designed to create a comprehensive, evidence-based digest of the current project workspace. It acts as a central synthesis point, pulling together historical context, active work streams, and immediate action items into one coherent report.

The core philosophy is that raw, verifiable workspace evidence must always take precedence over polished narrative or speculative content. This tool structures complex information flow for internal stakeholders who need to understand 'what happened,' 'what's happening,' and 'what needs to happen next.'

## Capabilities
*   **Multi-Source Synthesis:** Integrates data from Blueprint Knowledge (historical artifacts), Growth Studio mirror (current framing), and selected Work Queue views (action items).
*   **Digest Generation:** Creates a concise roundup structure suitable for weekly internal reporting.
*   **Action Item Identification:** Automatically drafts necessary follow-up work items if the synthesized digest clearly implies outstanding tasks.
*   **Contextual Handoffs:** Determines when the output should be passed to specialized agents like `metrics-reporter` or `growth-lead` based on the content's focus.

## Example Use Cases
*   **Weekly Sync Prep:** Running this agent every Friday to generate a digest summarizing all progress across the past week for leadership review.
*   **Project Handoff:** When one team is finishing and another is starting, use it to create a clean handoff document that summarizes completed artifacts and outstanding questions.
*   **Bottleneck Identification:** If the Work Queue shows several stalled items, running this digest can surface these bottlenecks alongside the relevant historical context from Blueprint Knowledge for immediate attention.