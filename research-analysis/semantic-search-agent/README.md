## Overview
This Semantic Search Agent is a powerful tool designed to ingest and query large volumes of unstructured text data. It moves beyond simple keyword matching by leveraging vector embeddings (specifically with PGVector) to understand the *meaning* behind user queries, providing highly relevant document chunks and synthesized summaries.

It features an intelligent routing mechanism that automatically decides whether a standard semantic search or a combined hybrid search will yield the best results, ensuring optimal retrieval accuracy for any given query type.

## Capabilities
*   **Semantic Retrieval**: Executes similarity searches using OpenAI embeddings to find contextually relevant documents.
*   **Intelligent Search Routing**: Automatically switches between pure semantic and hybrid (vector + full-text) search modes based on query analysis, or accepts manual overrides.
*   **Result Summarization**: Synthesizes information from multiple retrieved sources into concise, actionable summaries while maintaining clear source attribution for verification.
*   **Structured Interaction**: Maintains a clean Command Line Interface (CLI) experience for straightforward user interaction.

## Example Use Cases
1. **Market Trend Analysis**: Upload quarterly reports and ask, "What are the key risks identified in Q3 regarding supply chain dependencies?" The agent will semantically search all documents to synthesize a risk summary with source citations.
2. **Technical Documentation Query**: Given a large codebase manual, query, "How do I implement OAuth 2.0 flow using the new SDK version?" The agent uses hybrid search for precision and returns step-by-step instructions from relevant sections.
3. **Comparative Research**: Provide documents on two competing technologies and ask, "Compare the energy efficiency metrics of Technology A vs. Technology B." The agent summarizes the comparative data points found across all provided sources.