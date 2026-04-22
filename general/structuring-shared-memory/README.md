# Structuring Shared Memory

> Key Considerations for Structuring Shared Memory:

- **Layered Memory**: Think of different levels of memory, similar to human memory.
  - **Short-Ter

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
Key Considerations for Structuring Shared Memory:

- **Layered Memory**: Think of different levels of memory, similar to human memory.
  - **Short-Term Memory**: Focuses on the immediate context of interactions, such as ongoing conversations or task-related information. LangGraph is a framework that helps manage this by storing the conversation state.
  - **Long-Term Memory**: Houses historical interactions, conversation histories, and learned knowledge, enabling agents to remember user preferences and adapt to past experiences.
  - **Episodic Memory**: Allows agents to recall specific interactions or experiences, helping them understand context and build relationships over time.
  - **Semantic Memory**: Stores factual knowledge and domain-specific information, like product specifications or general knowledge.
- **Memory Types**: Consider diverse data formats and approaches for storing and retrieving information.
  - **File-based Memory**: Simple for storing context, using formats like JSON or Markdown for easy parsing.
  - **Database Integration (e.g., SQL, NoSQL)**: Provides structured storage for queryable memory, allowing agents to interact with the data through a natural language interface.
  - **Vector Databases (RAG systems)**: Ideal for storing large volumes of information that don't need to be constantly in the context window. Agents use semantic search to retrieve relevant information when needed.
  - **Knowledge Graphs**: Represent relationships between entities and facts, offering a more advanced way to organize and access knowledge.
- **Conflict Resolution**: Implement mechanisms to handle conflicting writes to shared memory from multiple agents.
  - **Event Sourcing**: Captures the history of memory changes, allowing for analysis and replaying of memory formation.
  - **Semantic Conflict Resolution**: Specialized agents review conflicting writes and generate coherent reconciliations, leveraging language model capabilities.
  - **CRDTs (Conflict-free Re

*[truncated — see source for full prompt]*