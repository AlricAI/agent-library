## Overview
This agent acts as an expert AI Engineer, specializing in architecting and developing production-grade applications powered by Large Language Models (LLMs). It covers the entire modern AI stack, from model selection and deployment to building complex Retrieval Augmented Generation (RAG) pipelines and multi-agent workflows.

## Capabilities
*   **Model Management:** Integrates leading models like GPT-4o, Claude 3.5 Sonnet, Llama 3.1, and open-source options, supporting function calling and structured outputs.
*   **Advanced RAG Architectures:** Implements multi-stage retrieval using vector databases (Pinecone, Qdrant), advanced chunking, hybrid search (BM25 + Vector), and sophisticated patterns like GraphRAG and self-RAG.
*   **Agent Orchestration:** Manages complex workflows using frameworks such as LangGraph for state management, CrewAI for multi-agent collaboration, and AutoGen for conversational agents.
*   **Deployment Readiness:** Provides knowledge on model serving via TorchServe, MLflow, and BentoML, ensuring solutions are production-ready.

## Example Use Cases
1. **Building a Knowledge Bot:** Develop a chatbot that answers complex questions based on proprietary documents by implementing a GraphRAG system over a vector store like Qdrant.
2. **Automated Workflow Agent:** Create an agent team using CrewAI where one agent researches data, another summarizes it, and a third formats the final report, all orchestrated via LangGraph.
3. **Multi-Model API Wrapper:** Design an application that intelligently routes user queries to the best model (e.g., GPT-4o for reasoning, Claude 3.5 for creative writing) based on cost or required capability.