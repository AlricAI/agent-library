# Tools

> """Search tools for Semantic Search Agent.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Search tools for Semantic Search Agent."""

import json
from typing import Any

from dependencies import AgentDependencies
from pydantic import BaseModel
from pydantic_ai import RunContext


class SearchResult(BaseModel):
    """Model for search results."""
    chunk_id: str
    document_id: str
    content: str
    similarity: float
    metadata: dict[str, Any]
    document_title: str
    document_source: str


async def semantic_search(
    ctx: RunContext[AgentDependencies],
    query: str,
    match_count: int | None = None
) -> list[SearchResult]:
    """
    Perform pure semantic search using vector similarity.

    Args:
        ctx: Agent runtime context with dependencies
        query: Search query text
        match_count: Number of results to return (default: 10)

    Returns:
        List of search results ordered by similarity
    """
    try:
        deps = ctx.deps

        # Use default if not specified
        if match_count is None:
            match_count = deps.settings.default_match_count

        # Validate match count
        match_count = min(match_count, deps.settings.max_match_count)

        # Generate embedding for query
        query_embedding = await deps.get_embedding(query)

        # Convert embedding to PostgreSQL vector string format
        embedding_str = '[' + ','.join(map(str, query_embedding)) + ']'

        # Execute semantic search
        async with deps.db_pool.acquire() as conn:
            results = await conn.fetch(
                """
                SELECT * FROM match_chunks($1::vector, $2)
                """,
                embedding_str,
                match_count
            )

        # Convert to SearchResult objects
        return [
            SearchResult(
                chunk_id=str(row['chunk_id']),
                document_id=str(row['document_id']),
                content=row['content'],
                similarity=row['similarity'],
                metadata=json.loads(row['metadata']) if row['meta

*[truncated — see source for full prompt]*