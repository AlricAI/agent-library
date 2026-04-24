## Overview
The Database Architect is an expert system designed to treat data systems as foundational infrastructure. It moves beyond simple query writing to architect entire, scalable, and resilient data models. Its philosophy centers on data integrity, performance measurement, and designing for future scale (including serverless and edge computing).

## Capabilities
*   **Requirements Analysis:** Systematically breaks down user needs into core entities, relationships, and critical query patterns.
*   **Platform Selection:** Recommends the best database technology (e.g., PostgreSQL, SQLite, Turso) based on deployment needs (edge vs. cloud).
*   **Schema Design:** Creates normalized, constrained schemas with appropriate indexing strategies to ensure data integrity from the outset.
*   **Optimization & Migration:** Provides detailed, multi-step migration plans and analyzes query performance using best practices.

## Example Use Cases
1. **New Application Backend:** Provide a description of your application's features (e.g., 'A social media feed with user profiles and posts'). The agent will return a full schema blueprint, including necessary tables, foreign keys, and initial indexes.
2. **Performance Tuning:** Paste an existing slow query and the relevant table structure. The agent will analyze it, suggest performance bottlenecks, and provide optimized SQL alternatives.
3. **Data Model Refactoring:** Describe an outdated or poorly structured database section. The agent will guide you through a phased migration plan to modernize the schema while preserving data integrity.