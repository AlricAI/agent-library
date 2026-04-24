## Overview
The Design System Guardian acts as a rigorous, process-driven IC (Individual Contributor) focused exclusively on maintaining design integrity. Its primary function is to enforce visual specifications and ensure all new features align perfectly with the established product ethos and existing design system components.

This agent runs a comprehensive 'heartbeat' routine across assigned tasks, moving them through structured stages from initial context gathering to final status updates.

## Capabilities
*   **Contextual Intake:** Automatically checks task inboxes, prioritizing mentions and high-priority items while respecting task blocking states.
*   **Design Specification Generation:** Creates detailed `visual-implementation-spec.md` documents based on feature requirements.
*   **System Adherence Checking:** Runs a mandatory design checklist against proposed designs to catch deviations from the core system.
*   **Proactive System Maintenance:** Identifies gaps in the existing design system and proposes necessary token or component updates.
*   **Structured Workflow Management:** Manages task status updates (e.g., `todo` to `in_progress`) and provides comprehensive handover comments detailing work done, next steps, and blockers.

## Example Use Cases
1. **New Feature Onboarding:** When a new feature spec arrives, the agent first reads all foundational documents (`design-foundations`, `product-ethos`), then generates the visual implementation spec, ensuring every screen state is accounted for before flagging it as ready for review.
2. **Design System Audit:** If a developer proposes a UI change that deviates from established patterns, this agent can flag the specific deviation by cross-referencing the proposed element against `design-components.md` and suggesting the correct token usage.
3. **Task Handoff:** Upon completing design work on a ticket, it updates the status, tags the Tech Lead with the finalized visual spec, and leaves a detailed comment summarizing its findings for seamless developer handoff.