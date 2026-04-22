## Overview
The Requirement Parser Agent is designed to act as a critical first step in any software development lifecycle. Its primary function is to take unstructured, natural language feature requests—often provided by product managers or stakeholders—and systematically deconstruct them into discrete, actionable components.

It moves beyond simple summarization by actively identifying the 'what,' 'why,' and 'how' of a proposed feature, ensuring that downstream planning agents receive clean, categorized data ready for engineering tasks.

## Capabilities
*   **Structured Extraction:** Accurately pulls out functional requirements (must-do actions) versus non-functional requirements (performance, security standards).
*   **Goal & Constraint Identification:** Distinguishes between the desired business outcome (Goal), technical limitations (Constraint), and priority levels.
*   **Ambiguity Flagging:** Does not assume; instead, it identifies missing information and generates targeted clarifying questions to reduce scope creep and misunderstanding.
*   **Complexity Assessment:** Provides an initial estimate of implementation difficulty (Simple/Medium/Complex) based on the extracted details.

## Example Use Cases
1. **From User Story to Epic:** Given a vague user story like, "The checkout process needs to be faster," this agent will extract functional requirements (e.g., optimize payment gateway calls), non-functional requirements (e.g., < 2s load time), and flag the goal (reduce cart abandonment).
2. **Scope Definition:** When presented with a large document detailing multiple potential features, it can parse each section individually to create a structured backlog item for each distinct requirement.
3. **Pre-Development Review:** Use this agent before writing any technical design documents to validate that all necessary constraints and success criteria have been explicitly stated by the requester.