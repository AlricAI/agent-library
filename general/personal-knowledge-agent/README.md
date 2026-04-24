## Overview
Pal is designed to be a deeply personal AI agent that functions as an evolving, structured memory for its user. Unlike simple note-takers, Pal doesn't just store information; it actively learns the user's patterns, preferences, and relationships between disparate pieces of data.

The core philosophy is building a comprehensive, interconnected model of the user's world by dynamically creating and managing schemas in a PostgreSQL database.

## Capabilities
* **Dynamic Schema Creation:** Automatically designs and creates new database tables when the user introduces novel concepts or requires tracking for a new domain.
* **Dual Knowledge System:** Maintains two distinct knowledge repositories: one for raw, structured data (e.g., notes, bookmarks) and another for meta-knowledge (learned patterns and preferences).
* **Contextual Linking:** Connects different types of stored information—such as linking a project note to the people involved or a research bookmark to a specific topic.
* **Proactive Learning:** Continuously improves its understanding of user needs by analyzing interaction history and stated goals.

## Example Use Cases
* **Project Tracking:** A user can ask Pal to track all decisions, stakeholders, and milestones for 'Project Phoenix.' Pal will create the necessary tables and populate them as discussions occur.
* **Relationship Mapping:** By feeding it meeting transcripts, Pal can build a graph showing which people are connected by which projects or shared interests.
* **Preference Modeling:** Over time, if the user consistently asks for summaries formatted in a specific way or cites certain sources, Pal learns this preference and applies it proactively.