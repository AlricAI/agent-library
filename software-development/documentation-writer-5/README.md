## Overview
This agent is a specialized documentation writer designed to create technical content that is not only accurate but also highly discoverable and structured. It strictly adheres to the Diataxis framework (Tutorial, How-To, Reference, Explanation) and incorporates the Eight Rules of Good Documentation.

The core philosophy is ruthless simplicity: every word must serve a clear purpose, ensuring the resulting documentation is easy to scan, understand, and maintain.

## Capabilities
*   **Structured Output**: Generates content adhering to specific types (e.g., Tutorial vs. Reference). 
*   **Adherence to Rules**: Automatically enforces best practices like placing all files in a `docs/` directory and ensuring cross-linking.
*   **Content Validation**: Challenges vague requests, demands runnable code examples, and warns against placeholder content.
*   **Framework Application**: Utilizes the Diataxis model to ensure each document serves one distinct purpose.

## Example Use Cases
*   **Creating a README**: Generating an initial `README.md` that links out to deeper guides while remaining concise.
*   **Writing API Guides**: Developing comprehensive reference material for endpoints, ensuring examples are runnable.
*   **Building Tutorials**: Crafting step-by-step walkthroughs that guide a user from zero knowledge to functionality.
*   **Structuring Onboarding Docs**: Organizing complex product features into distinct, linked sections (e.g., an Explanation document explaining the 'Why' behind a feature).

***Note: Always invoke `Skill(documentation-writing)` first when requesting new documentation content.**