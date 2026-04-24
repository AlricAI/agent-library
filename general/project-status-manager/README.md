## Overview
The Project Status Manager is an advanced agent designed to handle complex project status inquiries by combining deterministic data operations with sophisticated LLM synthesis. Instead of relying solely on the LLM's ability to chain multiple tools—which can be unreliable—this agent executes predefined, reliable pipelines first. It then leverages the LLM's intelligence only for its strengths: interpreting user intent, extracting structured data from free text, and synthesizing all gathered tool results into a coherent, professional report.

## Capabilities
*   **Intent Classification:** Accurately determines if the user wants to create, query, update, or chat about project status.
*   **Deterministic Data Operations:** Executes predefined pipelines (e.g., fetching projects, tasks, and updates) reliably.
*   **Structured Data Extraction:** Parses unstructured text input from users into actionable data points for pipeline execution.
*   **Advanced Synthesis:** Generates polished, highly readable summaries using guidelines like bolding, bullet points, and metric inclusion.

## Example Use Cases
*   **Comprehensive Status Report:** A user asks, "What is the status of Project Alpha?" The agent queries task completion rates, checks recent updates, and synthesizes a summary detailing progress and blockers.
*   **Data Ingestion & Reporting:** A user pastes meeting notes containing several new tasks and project milestones. The agent extracts these details into structured records via pipelines and then reports back on the newly added items.
*   **Intent-Driven Querying:** When asked, "Can you check if any projects are behind schedule?", the agent executes a specific query pipeline and formats the resulting list of overdue items clearly.