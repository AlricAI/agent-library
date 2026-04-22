# Memory Retrieval

> from __future__ import annotations

"""Memory retrieval using Kuzu backend for goal-seeking agents.

Philosophy:
- Single responsibility: Query memory

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
from __future__ import annotations

"""Memory retrieval using Kuzu backend for goal-seeking agents.

Philosophy:
- Single responsibility: Query memory system
- Uses amplihack-memory-lib with Kuzu backend
- Simple interface for text search
- Returns structured results for LLM consumption
"""

import re
from pathlib import Path
from typing import Any

from amplihack_memory import Experience, ExperienceStore, ExperienceType

_STRUCTURED_ID_PATTERN = re.compile(r'(?<!")\b([A-Z]{2,5}-\d{4}-\d{2,5})\b(?!")')


def _normalize_fts_query(query: str) -> str:
    """Normalize simple text queries before handing them to SQLite FTS5.

    SQLite FTS5 treats hyphenated identifiers like ``INC-2024-001`` as query
    syntax unless they are wrapped in double quotes. Quote structured IDs up
    front so direct ID lookups work in the same way as normal text queries.
    """
    normalized = query.strip()
    if not normalized:
        return normalized

    return _STRUCTURED_ID_PATTERN.sub(r'"\1"', normalized)


class MemoryRetriever:
    """Memory search interface using Kuzu graph database.

    Provides simple text-based search over stored experiences.
    Used by goal-seeking agents to retrieve relevant knowledge.

    Attributes:
        agent_name: Name of the agent (for memory isolation)
        connector: MemoryConnector to Kuzu backend
    """

    def __init__(self, agent_name: str, storage_path: Path | None = None, backend: str = "kuzu"):
        """Initialize memory retriever.

        Args:
            agent_name: Agent identifier (must not be empty)
            storage_path: Storage directory (defaults to ~/.amplihack/memory/<agent>)
            backend: Backend type ('kuzu' or 'sqlite', default: 'kuzu')

        Raises:
            ValueError: If agent_name is empty
        """
        if not agent_name or not agent_name.strip():
            raise ValueError("agent_name cannot be empty")

        self.agent_name = agent_name.strip()
        store_kwargs: dict[str, Any] =

*[truncated — see source for full prompt]*