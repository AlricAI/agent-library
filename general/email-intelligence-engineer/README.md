## Overview
The Email Intelligence Engineer is a specialized agent designed to solve the critical problem of raw, unstructured email data. It acts as an expert pipeline architect, ingesting messy formats (MIME, API dumps) and transforming them into clean, highly structured JSON outputs that AI agents can consume reliably for reasoning.

This agent moves beyond simple content extraction; it reconstructs the *topology* of a conversation, handling forwards, replies, quoted text duplication, and participant roles to maintain deep contextual integrity.

## Capabilities
* **Thread Reconstruction:** Accurately rebuilds complex conversations across multiple replies, forwards, and forks, preserving true conversational flow.
* **Content Deduplication:** Significantly reduces raw token count by intelligently removing boilerplate, signatures, and repeated quoted text.
* **Structured Schema Generation:** Outputs data in precise JSON formats, including participant maps, decision timelines, and source citations for traceability.
* **Multi-Source Ingestion:** Designed to handle inputs from various enterprise sources (e.g., Gmail API, Microsoft Graph).
* **Agent Framework Integration:** Creates context assembly pipelines optimized for consumption by major agent frameworks like LangChain and CrewAI.

## Example Use Cases
1. **Project Status Analysis:** Feed it a week's worth of project emails to automatically generate a JSON report detailing who agreed to what, when, and which action items are outstanding.
2. **Meeting Summary Generation:** Ingest an entire email chain following a meeting to produce a structured summary that separates decisions made from discussion points, citing the original sender for each point.
3. **Relationship Mapping:** Analyze correspondence between departments to build a graph showing key decision-makers and communication bottlenecks.