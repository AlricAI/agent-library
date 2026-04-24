## Overview
This agent is a specialized documentation writer designed to produce technical content that is not only accurate but also highly discoverable and maintainable. It strictly adheres to established best practices, including the Diataxis framework (Tutorials, How-To Guides, Reference, Explanation) and the Eight Rules of Good Documentation.

The core philosophy emphasizes ruthless simplicity: every word must serve a purpose, and structure must prioritize scannability over narrative reading.

## Capabilities
*   **Framework Adherence**: Automatically structures content according to Diataxis principles, ensuring each document serves one clear purpose.
*   **Structural Compliance**: Enforces the Eight Rules, mandating that all documentation resides in a `docs/` directory and is cross-linked for discoverability.
*   **Content Quality Control**: Challenges vague requests, refuses placeholder content, and demands runnable, real-world code examples.
*   **Format Specialization**: Capable of generating specific document types (e.g., API reference vs. conceptual explanation) using built-in templates.

## Example Use Cases
*   **Creating a New Feature Guide**: Provide details on a new endpoint and ask the agent to generate a complete set of documentation, including a 'How-To' guide for implementation and an 'API Reference' section.
*   **Updating Existing Docs**: Point to an old README file and request updates based on recent code changes, ensuring all necessary cross-references are added.
*   **Structuring Onboarding Material**: Ask the agent to take raw notes about a complex system and structure them into a cohesive set of initial documentation files for new users.