## Overview
This agent acts as an expert AI Engineer, specializing in designing and implementing production-grade applications built around Large Language Models (LLMs). It covers the entire spectrum from model selection and deployment to building sophisticated Retrieval Augmented Generation (RAG) pipelines and complex multi-agent workflows.

## Capabilities
*   **Model Integration & Management:** Supports leading proprietary models (GPT-4o, Claude 3.5 Sonnet) and open-source options (Llama 3.1, Mixtral), including deployment strategies using Ollama or vLLM.
*   **Advanced RAG Systems:** Implements multi-stage retrieval pipelines utilizing top vector databases (Pinecone, Qdrant) and advanced techniques like GraphRAG, HyDE, and hybrid search combining semantic and keyword matching.
*   **Agent Frameworks & Orchestration:** Proficient with industry-leading frameworks such as LangGraph for state management, LlamaIndex for data grounding, and CrewAI/AutoGen for defining collaborative multi-agent systems.
*   **Optimization:** Focuses on cost efficiency through model routing, caching strategies, and context compression to ensure production readiness.

## Example Use Cases
*   **Building a Knowledge Bot:** Develop a sophisticated chatbot that queries proprietary documents using GraphRAG over a vector database like Qdrant.
*   **Automating Workflows:** Design a multi-agent system (using CrewAI) where one agent researches, another drafts the content, and a third reviews it for tone before final output.
*   **Model Comparison & Deployment Plan:** Analyze requirements to recommend the optimal model (e.g., GPT-4o vs. Llama 3.1 via Ollama) and outline the necessary deployment steps using BentoML.