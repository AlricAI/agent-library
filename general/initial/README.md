# INITIAL

> ## Executive Summary
A simple yet powerful semantic search agent that leverages PGVector to provide intelligent document retrieval and summarized insi

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent Requirements: Semantic Search Agent

## Executive Summary
A simple yet powerful semantic search agent that leverages PGVector to provide intelligent document retrieval and summarized insights. The agent automatically chooses between semantic and hybrid search while maintaining a clean CLI interface for user interactions.

## Agent Classification
- **Type**: Tool-Enabled Agent with structured output capabilities
- **Complexity**: Medium
- **Priority Features**: 
  1. Semantic search with embeddings
  2. Intelligent search type selection
  3. Search result summarization

## Functional Requirements

### Core Functionality
1. **Semantic Search Operation**
   - Execute semantic similarity search using PGVector embeddings
   - Automatically generate query embeddings using OpenAI text-embedding-3-small (1536 dimensions)
   - Return top-k relevant document chunks with similarity scores
   - **Acceptance Criteria**: Successfully retrieve and rank documents by semantic similarity

2. **Hybrid Search with Auto-Selection**
   - Automatically determine when to use semantic vs hybrid search based on query characteristics
   - Allow manual override when user explicitly specifies search type
   - Combine vector similarity with full-text search for enhanced results
   - **Acceptance Criteria**: Intelligently route queries to optimal search method

3. **Search Result Summarization**
   - Analyze retrieved chunks and generate concise insights
   - Synthesize information from multiple sources into coherent summaries
   - Maintain source attribution for transparency
   - **Acceptance Criteria**: Provide meaningful summaries with proper source references

### Input/Output Specifications
- **Input Types**: 
  - Natural language queries via CLI
  - Optional search type specification ("semantic", "hybrid", or auto-detect)
  - Optional result limit (default: 10)
- **Output Format**: String responses with structured summaries and source citations
- **Validation Requirements**: Query l

*[truncated — see source for full prompt]*