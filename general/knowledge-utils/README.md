# Knowledge Utils

> from __future__ import annotations

"""Arithmetic validation, entity helpers, fact extraction utilities."""

import json
import logging
import re
from

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
from __future__ import annotations

"""Arithmetic validation, entity helpers, fact extraction utilities."""

import json
import logging
import re
from typing import TYPE_CHECKING, Any

if TYPE_CHECKING:
    pass

from .action_executor import calculate
from .prompt_utils import _get_llm_completion, _load_prompt
from .prompts import load_prompt

logger = logging.getLogger(__name__)


class KnowledgeUtilsMixin:
    """Mixin providing knowledge utilities for LearningAgent."""

    # Person and project detection constants
    _PERSON_DETAIL_CUES = (
        "allerg",
        "birthday",
        "degree",
        "favorite food",
        "hobby",
        "hometown",
        "personal information",
        "pet",
        "team",
    )
    _NON_PERSON_NAME_TOKENS = frozenset(
        {
            "affected",
            "allergies",
            "allergy",
            "award",
            "birthday",
            "center",
            "city",
            "climate",
            "competitor",
            "computer",
            "customer",
            "daily",
            "data",
            "database",
            "development",
            "difference",
            "discrepancy",
            "educational",
            "engineering",
            "estimate",
            "experience",
            "facilities",
            "favorite",
            "food",
            "framework",
            "gartner",
            "hiring",
            "hobby",
            "hometown",
            "incident",
            "indicators",
            "information",
            "innovation",
            "internal",
            "island",
            "market",
            "marketing",
            "migration",
            "nationality",
            "newsletter",
            "personnel",
            "personal",
            "pet",
            "pets",
            "preference",
            "product",
            "professional",
            "production",
            "project",
            "report",
           

*[truncated — see source for full prompt]*