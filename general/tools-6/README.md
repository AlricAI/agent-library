# Tools

> ## Tool Implementation Specifications

Based on the requirements from INITIAL.md, this agent needs 3 essential tools for semantic search functionality

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Tools for Semantic Search Agent

## Tool Implementation Specifications

Based on the requirements from INITIAL.md, this agent needs 3 essential tools for semantic search functionality with automatic search type selection.

### Tool 1: semantic_search

**Purpose**: Execute semantic similarity search using PGVector embeddings  
**Pattern**: `@agent.tool` (context-aware, needs database access)  
**Parameters**:
- `query` (str): The search query to find semantically similar content
- `limit` (int, default=10): Maximum number of results to return (1-50)

**Implementation Pattern**:
```python
@agent.tool
async def semantic_search(
    ctx: RunContext[AgentDependencies],
    query: str,
    limit: int = 10
) -> List[Dict[str, Any]]:
    """
    Perform semantic similarity search using vector embeddings.
    
    Args:
        query: Natural language search query
        limit: Maximum number of results (1-50)
    
    Returns:
        List of search results with content, similarity scores, and metadata
    """
```

**Functionality**:
- Generate query embedding using OpenAI text-embedding-3-small
- Call `match_chunks(query_embedding, match_count)` database function
- Return results with similarity scores above 0.7 threshold
- Handle database connection errors with retry logic
- Validate limit parameter (1-50 range)

**Error Handling**:
- Retry database connections up to 3 times
- Fallback to empty results if embedding generation fails
- Log search metrics for performance monitoring

### Tool 2: hybrid_search

**Purpose**: Execute combined semantic + keyword search for enhanced results  
**Pattern**: `@agent.tool` (context-aware, needs database access)  
**Parameters**:
- `query` (str): The search query for both semantic and text matching
- `limit` (int, default=10): Maximum number of results to return (1-50)
- `text_weight` (float, default=0.3): Weight for text search component (0.0-1.0)

**Implementation Pattern**:
```python
@agent.tool
async def hybrid_search(
    ctx: 

*[truncated — see source for full prompt]*