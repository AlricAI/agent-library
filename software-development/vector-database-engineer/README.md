## Overview
This specialized AI agent acts as an expert architect for building robust, scalable vector database systems. It possesses deep knowledge across industry-leading platforms like Pinecone, Qdrant, Weaviate, and pgvector, ensuring that the resulting search infrastructure meets demanding performance criteria.

The core focus is on moving beyond simple similarity lookups to engineer complete, production-ready semantic retrieval pipelines capable of handling massive datasets with low latency.

## Capabilities
*   **Multi-Database Architecture:** Selects and designs solutions for Pinecone (serverless), Qdrant (high-performance filtering), Weaviate (GraphQL integration), Milvus (distributed scale), and pgvector (SQL native).
*   **Advanced Embedding Strategy:** Recommends optimal embedding models from OpenAI, Voyage AI, or open-source libraries based on domain needs (e.g., finance, law).
*   **Index Optimization:** Implements best practices for index construction, including HNSW tuning, Product Quantization (PQ), and appropriate chunking strategies.
*   **Hybrid Search Implementation:** Builds sophisticated retrieval mechanisms by fusing vector similarity search with traditional keyword methods like BM25, often using Reciprocal Rank Fusion (RRF).

## Example Use Cases
1. **Building a Corporate Knowledge Base:** Architecting a RAG system that ingests millions of internal documents, chunking them semantically, embedding them using `text-embedding-3-large`, and storing/querying them in Weaviate for complex Q&A.
2. **Recommendation Engine:** Designing a product similarity search feature where user behavior vectors are stored in Pinecone, allowing real-time retrieval of similar items with metadata filtering (e.g., only show electronics).
3. **Legal Document Analysis:** Implementing a system that requires both semantic understanding and exact keyword matching across legal texts, utilizing a hybrid search approach combining vector distance with BM25 scoring.