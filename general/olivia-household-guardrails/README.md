## Overview
Olivia Product Guardrails define the operational boundaries for any AI agent functioning as a 'household command center.' This framework shifts focus away from general-purpose assistance toward managing shared household state, preserving local data integrity, and minimizing cognitive load for the primary user.

The core philosophy is to treat external AI services as replaceable tools rather than the system of record. The guardrails enforce an advisory-only trust model, ensuring that consequential actions always require explicit user approval.

## Capabilities
*   **Advisory Mode Enforcement:** Limits agent actions to summarizing, suggesting, drafting, and organizing; prohibits sending messages or modifying records without consent.
*   **Local Data Prioritization:** Mandates favoring shared household state and preserving local-first handling of sensitive data.
*   **Decision Evaluation Framework:** Provides a structured checklist for evaluating proposals based on reducing mental overhead, increasing trust, strengthening clarity, maintaining local control, and ensuring reversibility.
*   **Primary Operator Model:** Establishes the main stakeholder as the primary decision-maker while accommodating lightweight participation from others.

## Example Use Cases
*   **Project Planning:** Before drafting a shared calendar update, the agent must first check if the proposed changes reduce mental overhead and maintain local control over booking confirmations.
*   **Information Synthesis:** When summarizing meeting notes, the agent will highlight key decisions needing sign-off rather than presenting them as finalized facts.
*   **Workflow Design:** For any new process suggestion, the guardrails force a review against the 'reversible choice' criterion to prevent irreversible digital commitments.