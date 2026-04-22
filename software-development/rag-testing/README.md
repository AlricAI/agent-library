# RAG TESTING

> ## Overview

The RAG (Retrieval Augmented Generation) Testing Suite is a comprehensive test framework designed to evaluate and validate the performanc

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# RAG Testing Suite Documentation

## Overview

The RAG (Retrieval Augmented Generation) Testing Suite is a comprehensive test framework designed to evaluate and validate the performance and quality of the RAG system implementation in ModPorter AI. This suite ensures that the AI agents can effectively retrieve and utilize knowledge from specialized knowledge bases.

## Architecture

The RAG system consists of several key components:

### Core Components

1. **RAG Crew (`src/crew/rag_crew.py`)**
   - Multi-agent system using CrewAI
   - Configurable agents with specialized roles
   - Dynamic tool assignment and agent communication

2. **Embedding Generator (`src/utils/embedding_generator.py`)**
   - Text embedding generation using sentence-transformers
   - Handles document vectorization for semantic search
   - Integrated with the JavaAnalyzerAgent for mod analysis

3. **Vector Database Client (`src/utils/vector_db_client.py`)**
   - Interface to PostgreSQL with pgvector extension
   - Document indexing and similarity search
   - Async operations for scalability

4. **Search Tool (`src/tools/search_tool.py`)**
   - Semantic search functionality
   - Document retrieval and filtering
   - Integration with knowledge base agents

5. **RAG Evaluator (`src/testing/rag_evaluator.py`)**
   - Evaluation framework for RAG system quality
   - Retrieval hit rate calculations
   - Performance metrics and reporting

## Testing Framework

### Test Structure

The testing suite is organized into several layers:

#### 1. Unit Tests (`tests/unit/`)

- **`test_rag_crew.py`**: Tests for RAG crew initialization, configuration, and agent setup
- **`test_embedding_generator.py`**: Tests for embedding generation, model loading, and error handling
- **`test_search_tool.py`**: Tests for search functionality, query processing, and result formatting
- **`test_vector_db_client.py`**: Tests for database operations, document indexing, and retrieval
- **`test_rag_evaluator.py`**: Tests for evaluati

*[truncated — see source for full prompt]*