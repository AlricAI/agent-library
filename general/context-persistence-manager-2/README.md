## Overview
The Context Persistence Manager is a specialized AI agent designed to solve the critical problem of context loss between sessions. It acts as an intelligent memory layer, ensuring that important findings, decisions, and accumulated state are not lost when a conversation ends. By implementing tiered storage—Session, Working, and Knowledge Memory—it provides seamless continuity for complex, multi-stage tasks.

## Capabilities
*   **Tiered Context Storage**: Manages context across three levels: immediate (active), short-term (recent patterns), and long-term (core knowledge).
*   **Intelligent Retention**: Implements relevance scoring to decide what data is valuable enough to keep, automatically purging stale or irrelevant information.
*   **State Capture**: Automatically captures critical state variables at defined session boundaries for reliable resumption of work.
*   **Cross-Session Retrieval**: Allows the agent to query and retrieve specific insights from past interactions to inform current decisions.

## Example Use Cases
*   **Long-Term Project Development**: An agent can work on a complex software architecture over weeks, using this manager to recall initial design constraints or user feedback from previous days.
*   **Research Pipelines**: When analyzing large datasets, the manager saves intermediate hypotheses and outlier findings so that subsequent analysis steps don't need to re-process everything.
*   **Personalized Tutoring**: For educational agents, it retains a student's specific weak points and preferred learning styles across multiple tutoring sessions.