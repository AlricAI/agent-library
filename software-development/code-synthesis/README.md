# Code Synthesis

> from __future__ import annotations

"""LLM-driven code generation for temporal queries."""

import json
import logging
from typing import TYPE_CHECKIN

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
from __future__ import annotations

"""LLM-driven code generation for temporal queries."""

import json
import logging
from typing import TYPE_CHECKING, Any

if TYPE_CHECKING:
    pass

from .prompt_utils import _get_llm_completion, _load_prompt
from .prompts import load_prompt

logger = logging.getLogger(__name__)


class CodeSynthesisMixin:
    """Mixin providing code synthesis for LearningAgent."""

    def temporal_code_synthesis(
        self,
        question: str,
        entity: str,
        field: str,
        candidate_facts: list[dict[str, Any]] | None = None,
    ) -> dict[str, Any]:
        """Generate Python code to resolve a temporal question deterministically.

        Produces a code snippet that retrieves the transition chain for
        the entity/field and either indexes into it based on the temporal
        keywords in the question or counts the number of transitions.

        Args:
            question: The temporal question text
            entity: Entity name (e.g., "Atlas project")
            field: Field name (e.g., "deadline")

        Returns:
            Dict with:
                - code: Generated Python code string
                - index_expr: The resolved expression used to answer
                - transitions: The actual transition chain retrieved
                - result: The resolved value (if chain is non-empty)
        """
        question_lower = question.lower()
        change_count_question = (
            "how many times" in question_lower
            or "how many changes" in question_lower
            or "number of changes" in question_lower
        ) and any(
            token in question_lower
            for token in ("change", "changed", "update", "updated", "modification")
        )
        index_expr = (
            "max(0, len(transitions) - 1)"
            if change_count_question
            else self._parse_temporal_index(question)
        )

        # Generate the code snippet
        code_lines = [
            

*[truncated — see source for full prompt]*