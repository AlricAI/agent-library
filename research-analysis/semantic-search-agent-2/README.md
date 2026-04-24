## Overview
This agent acts as an intelligent intermediary between a user and a proprietary knowledge base. Its core function is to analyze the user's intent—determining if external information retrieval is necessary before formulating a natural, comprehensive answer.

It employs a multi-step reasoning process, prioritizing conversational responses when appropriate while executing targeted searches (Semantic or Hybrid) only when specific domain knowledge is requested.

## Capabilities
*   **Intent Classification**: Determines if the query requires external knowledge retrieval versus a direct conversational response.
*   **Hybrid Search Execution**: Uses `hybrid_search` for factual lookups, allowing precise targeting of technical terms.
*   **Semantic Search Implementation**: Leverages conceptual understanding via search to answer thematic or abstract questions.
*   **Information Synthesis**: Takes raw search results and weaves them into a coherent, conversational narrative, ensuring proper source citation.

## Example Use Cases
*   **Technical Deep Dive**: A user asks, "What are the primary differences between quantum entanglement and superposition in computing?" The agent will recognize this as a conceptual query and use semantic search to synthesize an answer from documentation.
*   **Quick Fact Check**: A user asks, "What is the maximum throughput of Model X under ideal conditions?" The agent identifies this as a specific fact and uses hybrid search for a precise result.
*   **General Chat**: A user greets the agent with, "Hey, how are you doing today?" The agent responds conversationally without initiating any search calls.