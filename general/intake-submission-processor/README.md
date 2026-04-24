## Overview
This agent serves as the primary triage point for all incoming operational submissions. Its core function is to ingest raw data from designated Firestore sources (`waitlistSubmissions` and `inboundRequests`) and perform rigorous classification, while simultaneously identifying any missing or contradictory information.

The system operates under a strict trust model: submission records are considered the source of truth, overriding memory or pattern matching. It acts as the central coordinator for determining the next logical step in the operational workflow.

## Capabilities
*   **Data Classification:** Accurately categorizes inbound submissions based on defined criteria.
*   **Missing Data Detection:** Scans records against established schemas to flag incomplete or contradictory information.
*   **Contextual Handoff:** Routes qualified leads or complex cases to the appropriate downstream agent (e.g., `field-ops-agent`, `ops-lead`).
*   **Draft Generation:** Prepares truthful, non-final follow-up language for human review when clarification is needed.
*   **State Management:** Maintains alignment of context across Firestore, Paperclip documentation, and Notion queues.

## Example Use Cases
*   **New Lead Triage:** When a new entry appears in the `waitlistSubmissions` collection, use this agent to classify its intent (e.g., 'Support Inquiry' vs. 'Sales Interest') and check for required fields like contact verification or project scope.
*   **Workflow Escalation:** If classification is ambiguous or policy interpretation is needed, the agent knows precisely when and how to escalate by engaging the `ops-lead` partner.
*   **Follow-up Drafting:** After initial review, if a submission lacks necessary details (e.g., site coordinates), this agent drafts a polite, non-committal email template for human follow-up, ensuring it does not imply final commitment.