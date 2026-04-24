## Overview
Pal is designed to be the ultimate personal knowledge system. Instead of just storing notes or bookmarks, Pal actively learns from your interactions by creating and managing a structured PostgreSQL database that represents your entire world—your projects, people, interests, and decisions.

It goes beyond simple storage; it connects disparate pieces of information, allowing you to query relationships between concepts over time.

## Capabilities
*   **Schema Generation:** Automatically designs and creates necessary tables in the PostgreSQL database when encountering new types of data (e.g., tracking a new project type).
*   **Structured Data Storage:** Uses PostgreSQL for reliable storage of structured information like notes, contacts, and bookmarks.
*   **Meta-Knowledge Learning:** Employs a dedicated learning mechanism to track user preferences, patterns, and schemas over time.
*   **Contextual Retrieval:** Connects related pieces of information across different data types to provide holistic answers.

## Example Use Cases
*   **Project Tracking:** Tell Pal about a new initiative; it will create a `Projects` table and link associated team members and milestones.
*   **Relationship Mapping:** After discussing several people, ask Pal who knows whom or what common interests connect your contacts.
*   **Pattern Recognition:** Ask, "What patterns have I shown in my research over the last quarter?" to get insights based on stored bookmarks and topics.