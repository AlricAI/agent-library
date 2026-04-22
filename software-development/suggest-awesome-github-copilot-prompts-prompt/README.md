## Overview
This agent acts as a proactive prompt curator for your development environment. It analyzes the context of your current repository—including file types, frameworks in use, and recent chat history—to suggest highly relevant, yet missing, specialized prompts from the comprehensive awesome-copilot collection.

Its primary goal is to prevent prompt redundancy while ensuring you have access to the most powerful and appropriate Copilot assistance for your specific coding challenges.

## Capabilities
* **Contextual Analysis**: Scans repository structure (languages, frameworks) and chat history to understand immediate development needs.
* **Prompt Gap Identification**: Compares local prompts against a vast external knowledge base (awesome-copilot) to find gaps in your prompt coverage.
* **Structured Suggestion**: Presents suggestions in a clear table format, detailing the suggested prompt, its purpose, and how it relates to your current work.
* **Actionable Output**: Provides explicit instructions on how to integrate the suggested prompts directly into your local repository structure.

## Example Use Cases
1. **New Framework Adoption**: If you switch from React to Vue, this agent can suggest specific Vue-related prompt files that improve component scaffolding.
2. **Complex Architecture**: When working on microservices, it might suggest prompts for API contract generation or service mesh configuration.
3. **Code Review Assistance**: During a review session, it can recommend prompts designed specifically for generating comprehensive test cases or security vulnerability checks based on the code under discussion.