# Temporal Reasoning

> from __future__ import annotations

"""Temporal state tracking, transition chains, and chronological reasoning."""

import itertools
import logging
im

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
from __future__ import annotations

"""Temporal state tracking, transition chains, and chronological reasoning."""

import itertools
import logging
import re
from collections import defaultdict
from typing import TYPE_CHECKING, Any

if TYPE_CHECKING:
    pass

logger = logging.getLogger(__name__)


class TemporalReasoningMixin:
    """Mixin providing temporal reasoning for LearningAgent."""

    # Keyword-to-index mapping for temporal state resolution
    _TEMPORAL_KEYWORDS: dict[str, str] = {
        "first": "0",
        "original": "0",
        "initial": "0",
        "second": "1",
        "third": "2",
        "intermediate": "len(transitions) // 2",
        "middle": "len(transitions) // 2",
        "between": "len(transitions) // 2",
        "latest": "-1",
        "current": "-1",
        "final": "-1",
        "last": "-1",
    }

    # Temporal pattern constants
    _TEMPORAL_DATE_VALUE_PATTERN = re.compile(
        r"\b("
        r"(?:January|February|March|April|May|June|July|August|September|October|November|December)"
        r"\s+\d{1,2}(?:,\s+\d{4})?"
        r")\b"
    )
    _DEADLINE_DIRECT_VALUE_PATTERNS = (
        re.compile(
            r"\b(?:current|latest|final|last|original|initial)\s+deadline\s+"
            r"(?:is|was|of)\s+(?P<fragment>.+)$",
            re.IGNORECASE,
        ),
        re.compile(
            r"\bdeadline\s+(?:is|was|of)\s+(?P<fragment>.+)$",
            re.IGNORECASE,
        ),
        re.compile(
            r"\bdeadline\s+(?:has\s+been\s+)?(?:changed|moved|pushed|extended|updated)"
            r"(?:\s+again)?\s+to\s+(?P<fragment>.+)$",
            re.IGNORECASE,
        ),
        re.compile(
            r"\btarget\s+(?:delivery\s+)?date\s+(?:is|was|of)\s+(?P<fragment>.+)$",
            re.IGNORECASE,
        ),
    )
    _DIRECT_TEMPORAL_LOOKUP_PATTERN = re.compile(
        r"^\s*(?:what|who)\s+(?:is|was)\s+the\s+"
        r"(?P<qualifier>current|latest|original|initial|previous|final|last)\s+"
        r"(?P<fiel

*[truncated — see source for full prompt]*