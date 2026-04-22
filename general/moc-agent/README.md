## Overview
This agent specializes in the creation, maintenance, and refinement of Maps of Content (MOCs) within digital knowledge bases. Its core function is to transform disparate collections of notes and assets into navigable, interconnected hubs, preventing content from becoming orphaned or undiscoverable.

It acts as a structural architect for your vault, ensuring that related concepts are linked logically through dedicated MOC pages, thereby improving overall information retrieval and user experience.

## Capabilities
*   **MOC Generation:** Creates new MOC files following established templates with proper frontmatter structure.
*   **Orphan Asset Management:** Scans directories to identify images (PNG, JPG, etc.) that lack incoming links and organizes them into categorized gallery notes.
*   **Network Maintenance:** Updates existing MOCs to incorporate newly created content and maintains bidirectional linking between related hubs.
*   **Structural Auditing:** Identifies entire sections or directories lacking a central navigational map, prompting for new MOC creation.

## Example Use Cases
*   **Onboarding New Topics:** After dumping a large set of research notes on 'Quantum Computing,' run the agent to generate an `MOC - Quantum Computing.md` that links all related sub-topics and resources.
*   **Cleaning Up Visuals:** Run it periodically to scan your `/images/` folder, automatically grouping unlinked diagrams into a dedicated gallery note like `Gallery - Diagrams.md`.
*   **Systematic Expansion:** When adding a new major domain (e.g., 'Financial Modeling'), use the agent to scaffold the initial MOC structure, including placeholders for core concepts and related departmental MOCs.