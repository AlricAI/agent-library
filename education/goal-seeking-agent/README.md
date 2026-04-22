# Goal Seeking Agent

> from __future__ import annotations

"""GoalSeekingAgent — OODA loop interface over the LearningAgent internals.

Philosophy:
- Single agent type with 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
from __future__ import annotations

"""GoalSeekingAgent — OODA loop interface over the LearningAgent internals.

Philosophy:
- Single agent type with a universal OODA loop (Observe-Orient-Decide-Act).
- Content and questions are both just *input*. The agent classifies and handles
  them internally. The caller never calls learn_from_content() or
  answer_question() directly.
- Output (answers) goes to stdout/log. In distributed mode Container Apps
  streams this to Log Analytics. The eval reads from there — no Service Bus
  round-trip for answers.
- LearningAgent is an implementation detail; GoalSeekingAgent is the public API.

Public API:
    observe(input_data)  → store raw input, start OODA cycle
    orient()             → recall relevant facts from memory → dict
    decide()             → classify as "store" | "answer"
    act()                → execute decision, write output to stdout → str
    process(input_data)  → observe → orient → decide → act pipeline → str
    process_store(input_data) → observe → force-store → act pipeline → str
    learn_from_content(input_data) → benchmark/eval compatibility delegate
    answer_question(question) → benchmark/eval compatibility delegate

Backward compatibility:
    LearningAgent is NOT removed; existing callers continue to work unchanged.
"""

import asyncio
import inspect
import logging
from pathlib import Path
from typing import Any

from .retrieval_constants import ORIENT_SEARCH_LIMIT

logger = logging.getLogger(__name__)


def _run_maybe_async(value: Any) -> Any:
    """Run coroutine-like values, otherwise return them unchanged."""
    if inspect.isawaitable(value):
        return asyncio.run(value)
    return value

# Minimal sentinel so orient/decide/act can be called without prior observe()
_NO_INPUT = object()
_QUESTION_PREFIXES = (
    "what ",
    "who ",
    "when ",
    "where ",
    "why ",
    "how ",
    "which ",
    "is ",
    "are ",
    "was ",
    "were ",
    "do ",
    "does ",
    "did ",
    "can

*[truncated — see source for full prompt]*