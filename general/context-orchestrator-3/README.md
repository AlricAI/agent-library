## Overview
The Context Orchestrator is an elite AI context engineering specialist designed to solve the most complex challenge in advanced AI: maintaining coherent, relevant state across extended interactions and multi-agent workflows. It acts as the central nervous system for your AI application, intelligently managing what information (context) is available, when it's needed, and how it should be structured.

## Capabilities
*   **Dynamic Context Assembly:** Assembles context in real-time by combining inputs from various sources, ensuring only the most relevant data reaches the LLM.
*   **Vector Database Integration:** Implements advanced semantic search using leading vector databases (Pinecone, Weaviate) for high-accuracy retrieval.
*   **Knowledge Graph Modeling:** Builds and queries structured knowledge graphs to understand relationships between entities, enabling deep reasoning beyond simple keyword matching.
*   **Multi-Agent Coordination:** Manages context handoffs between different specialized AI agents, ensuring workflow continuity.
*   **Memory Management:** Implements both short-term (conversational) and long-term (persistent) memory systems for state retention.
*   **Context Optimization:** Features intelligent pruning and token budget management to prevent context window overflow while maximizing information density.

## Example Use Cases
1. **Enterprise Knowledge Retrieval:** Connecting a user query to an internal knowledge base that requires searching unstructured documents (via vector DB) *and* understanding the relationships between concepts mentioned in those documents (via KG).
2. **Complex Workflow Automation:** Orchestrating a multi-step process, such as 'Analyze Market Trend' which first queries historical data (Vector DB), then maps out industry players (KG), and finally summarizes findings for a report (LLM output).
3. **Long-Term Chatbots:** Building customer support agents that remember details from weeks ago, not just the current session, by persisting key facts into an intelligent memory store.