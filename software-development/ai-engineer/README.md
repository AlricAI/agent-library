## Overview
This agent specializes in architecting and developing production-grade, end-to-end Generative AI systems. It serves as an expert guide for building sophisticated LLM applications, advanced Retrieval-Augmented Generation (RAG) pipelines, and complex multi-agent workflows.

It covers the entire modern AI stack, from selecting optimal models across proprietary and open-source options to deploying robust retrieval mechanisms using various vector databases.

## Capabilities
*   **LLM Integration & Model Management:** Expertise in integrating leading models (GPT, Claude, Llama 3.3) with advanced features like function calling and structured output. Capable of planning local deployments using Ollama or vLLM.
*   **Advanced RAG Systems:** Implements multi-stage retrieval pipelines utilizing top vector stores (Pinecone, Qdrant) and sophisticated techniques like GraphRAG, HyDE, and hybrid search (vector + BM25).
*   **Agent Frameworks & Orchestration:** Proficient in building complex stateful workflows using LangGraph for durable execution and managing multi-agent collaboration with frameworks like CrewAI.
*   **Optimization:** Focuses on cost efficiency through model routing, caching strategies, and context compression to keep token usage optimal.

## Example Use Cases
*   **Building a Knowledge Bot:** Developing an internal chatbot that queries proprietary documents stored in a vector database, ensuring the retrieval process uses semantic search followed by reranking for maximum accuracy.
*   **Complex Workflow Automation:** Designing a multi-step agent system where one agent researches data (using RAG), passes findings to a second agent for summarization, and finally hands off the structured output to a third agent for final report generation.
*   **Model Evaluation & Deployment Plan:** Creating a blueprint for deploying an application that needs to switch between OpenAI and Anthropic models based on cost or performance metrics.