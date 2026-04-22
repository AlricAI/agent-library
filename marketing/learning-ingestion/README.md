# Learning Ingestion

> from __future__ import annotations

"""Content ingestion, fact extraction, and storage logic."""

import json
import logging
import re
from typing imp

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
from __future__ import annotations

"""Content ingestion, fact extraction, and storage logic."""

import json
import logging
import re
from typing import TYPE_CHECKING, Any

if TYPE_CHECKING:
    pass

from .prompt_utils import _get_llm_completion, _load_prompt
from .prompts import load_prompt

logger = logging.getLogger(__name__)


class LearningIngestionMixin:
    """Mixin providing content ingestion for LearningAgent."""

    async def learn_from_content(self, content: str) -> dict[str, Any]:
        """Learn from content by extracting and storing facts.

        When use_hierarchical=True, stores the raw content as an episode first,
        then extracts facts with source_id pointing to the episode for provenance.
        Detects temporal markers in content and attaches temporal metadata to facts.

        Args:
            content: Article or content text

        Returns:
            Dictionary with learning results:
                - facts_extracted: Number of facts extracted
                - facts_stored: Number of facts stored
                - content_summary: Summary of content

        Example:
            >>> agent = LearningAgent()
            >>> result = agent.learn_from_content(
            ...     "Photosynthesis converts light into chemical energy."
            ... )
            >>> print(result['facts_extracted'])  # 1
        """
        batch = await self.prepare_fact_batch(content)
        return self.store_fact_batch(batch, record_learning=True)

    @staticmethod
    def _truncate_learning_content(content: str) -> str:
        """Trim oversized learning content to the safe maximum length."""
        max_content_length = 50_000
        if len(content) > max_content_length:
            logger.warning(
                "Content truncated from %d to %d chars", len(content), max_content_length
            )
            return content[:max_content_length]
        return content

    @staticmethod
    def _extract_source_label(content: str) -> str:

*[truncated — see source for full prompt]*