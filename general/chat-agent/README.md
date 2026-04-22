# Chat Agent

> """
Chat Agent.

A versatile chat agent with access to multiple tools for comprehensive assistance.
Uses LLM-driven tool selection to proactively help

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Chat Agent.

A versatile chat agent with access to multiple tools for comprehensive assistance.
Uses LLM-driven tool selection to proactively help users with various tasks.

This agent extends BaseStreamingAgent with multi-tool access and LLM-driven
tool selection strategy.
"""

import asyncio
import inspect
import json
import logging
import time
from typing import Any, Dict, List, Optional, Set

from app.agents.base_agent import (
    AgentConfig,
    AgentContext,
    BaseStreamingAgent,
    ExecutionMode,
    PipelineStep,
    TOOL_CLASSES,
    TOOL_CLASS_DEFAULT,
    ToolRegistry,
    ToolStrategy,
)
from app.schemas.streaming import clarify_parallel, content, error, interim, plan, progress, prompt, thought
from pydantic import BaseModel, ValidationError

from busibox_common.llm import get_client

import re

logger = logging.getLogger(__name__)

_THINK_RE = re.compile(r"<think>(.*?)</think>", re.DOTALL)

_YES_NO_PATTERNS = [
    re.compile(r"\bwould you like me to\b"),
    re.compile(r"\bshall i\b"),
    re.compile(r"\bdo you want me to\b"),
    re.compile(r"\bshould i\b"),
    re.compile(r"\bwould you like to\b(?!\s+\w+\s+or\b)"),
]


def _ends_with_yes_no_question(text: str) -> bool:
    """Return True if *text* ends with a genuinely binary yes/no question.

    Excludes choice questions that contain "or" (e.g., "do you prefer X or Y?")
    since those need open-ended answers, not yes/no buttons.
    """
    stripped = text.rstrip()
    if not stripped.endswith("?"):
        return False
    last_sentence = stripped.rsplit("\n", 1)[-1].lower()
    if " or " in last_sentence:
        return False
    return any(p.search(last_sentence) for p in _YES_NO_PATTERNS)


def _strip_think_tags(text: str) -> tuple:
    """Strip ``<think>`` blocks and return (clean_text, think_content_or_None)."""
    matches = _THINK_RE.findall(text)
    if not matches:
        return text, None
    think_text = "\n".join(m.strip() for m in matches)
    cleaned = _THINK_RE.sub("", te

*[truncated — see source for full prompt]*