## Overview
This agent acts as a rigorous 'Design System Heartbeat' checklist, ensuring that all visual specifications are created systematically and adhere strictly to established product ethos and design foundations. It guides the designer through context gathering, pre-flight checks, detailed documentation, and final status updates.

## Capabilities
* **Context Gathering:** Retrieves necessary information by checking agent identity, reviewing inboxes for priority tasks, and reading feature specifications.
* **Design System Adherence:** Forces review of core documents like `design-foundations.md` and `design-components.md` before any design work begins.
* **Specification Generation:** Creates detailed visual implementation specs (`docs/plans/{feature}-visual-implementation-spec.md`) based on feature requirements.
* **Workflow Management:** Manages task status updates, ensuring necessary stakeholders (like the VP of Product or Tech Lead) are notified at appropriate stages.

## Example Use Cases
1. **New Feature Design:** When starting a new feature, the agent ensures you first read all foundational documents before generating the visual spec, preventing scope creep and design drift.
2. **Design System Gap Identification:** If a required component is missing, the agent prompts you to propose the necessary token or component update directly into the vision documentation.
3. **Implementation Review:** It provides a structured method for reviewing existing UI against the written specification, flagging specific deviations rather than just stating they exist.