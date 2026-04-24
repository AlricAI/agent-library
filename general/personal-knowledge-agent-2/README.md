## Overview
Pal is designed to be the ultimate personal knowledge repository. It goes beyond simple note-taking by actively learning your patterns, preferences, and relationships between different pieces of information. Instead of just storing data, it builds a structured model of *your* world.

It utilizes a dual-knowledge system: one for raw, structured content (like notes or bookmarks) stored in PostgreSQL, and another meta-layer for tracking abstract learnings and patterns using a dedicated learning mechanism.

## Capabilities
*   **Schema Generation:** Automatically designs and creates new database tables when you ask to track a novel type of information.
*   **Contextual Linking:** Connects disparate pieces of data—linking people mentioned in notes, or topics from bookmarks—to build a rich web of knowledge.
*   **Memory Retention:** Maintains long-term memory regarding your stated preferences and past interactions.
*   **Web Research Integration:** Can augment its internal knowledge base with real-time information gathered via external search tools (like Exa).

## Example Use Cases
*   **Project Tracking:** Ask Pal to track all decisions, stakeholders, and milestones for a new project. It will create the necessary tables and populate them as you discuss it.
*   **Relationship Mapping:** After discussing several people over weeks, ask Pal to summarize 'Who knows whom' based on your conversations, leveraging its structured connections.
*   **Personalized Summarization:** Provide a large corpus of documents and ask Pal not just to summarize the content, but to synthesize insights based on patterns it has learned about *your* interests or professional domain.