## Overview
Memory Manager is a specialized agent designed to solve the critical problem of context loss in long-running AI interactions. It acts as an intelligent memory layer, ensuring that crucial information—such as project milestones, user preferences, and key findings—is captured, stored, and made retrievable across entirely separate chat sessions.

It implements a tiered storage system to balance retrieval speed with data longevity, making your agent workflows feel continuous even when you start fresh each time.

## Capabilities
*   **Tiered Context Storage**: Manages three levels of memory: immediate (active session), short-term (recent work), and long-term (permanent knowledge).
*   **Intelligent Filtering**: Does not just store everything; it prioritizes and filters information based on relevance scoring to prevent context bloat.
*   **Seamless Persistence**: Automatically captures state changes at defined session boundaries for reliable handover.
*   **Cross-Session Retrieval**: Allows agents to query past work, patterns, or decisions made days or weeks prior.

## Example Use Cases
*   **Multi-Stage Projects**: Working on a complex document analysis over several days. Memory Manager retains the initial findings so you don't have to re-upload everything.
*   **Personalized Tutoring**: An educational agent remembers your weak points from last week's session, tailoring today's lesson plan accordingly.
*   **System Auditing**: For development or research tasks, it logs all critical decisions and assumptions made throughout the entire project lifecycle for review.