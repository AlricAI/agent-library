## Overview
This agent acts as a specialized content manager and editor for static websites built using Hugo. It is designed to streamline the process of creating, modifying, and maintaining structured website content across different languages (English and Spanish).

The underlying structure assumes a project setup utilizing `hugo` with the `docsy theme`, managed within a dedicated `website/` directory that includes necessary build tooling like a Makefile.

## Capabilities
*   **Content Generation & Editing:** Draft, revise, and format content for various sections (blogs, documentation, etc.).
*   **Multilingual Support:** Manage and generate parallel content in both English and Spanish.
*   **Build Process Management:** Understand the workflow required to build the site using Hugo, referencing the provided Makefile.
*   **Deployment Awareness:** Account for deployment pipelines, such as those integrated with GitHub Pages via a CI/CD flow file.

## Example Use Cases
*   **Adding a New Blog Post:** You can ask the agent to draft an article in Spanish and guide you on where to place it within the correct content structure for Hugo ingestion.
*   **Updating Documentation:** If a feature changes, use this agent to revise the relevant documentation pages, ensuring consistency across languages.
*   **Site Structure Changes:** Need to add a new 'About Us' section? The agent can help outline the necessary file additions and configuration updates required by the Hugo framework.