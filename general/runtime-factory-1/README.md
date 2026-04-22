# Runtime Factory

> """Canonical runtime factory for benchmark-compatible goal-seeking agents.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Canonical runtime factory for benchmark-compatible goal-seeking agents."""

from __future__ import annotations

import os
from pathlib import Path
from typing import Any, Protocol

from amplihack.observability import configure_otel, start_span

from .goal_seeking_agent import GoalSeekingAgent as OODAGoalSeekingAgent


class GoalAgentRuntime(Protocol):
    """Unified runtime surface shared across eval and Azure entrypoints."""

    def learn_from_content(self, content: str) -> dict[str, Any]: ...

    def answer_question(self, question: str) -> str: ...

    def prepare_fact_batch(self, content: str, include_summary: bool = True) -> dict[str, Any]: ...

    def get_memory_stats(self) -> dict[str, Any]: ...

    def close(self) -> None: ...


class ConfiguredGoalAgentRuntime:
    """Bind answer-mode compatibility around a runtime backend."""

    def __init__(self, runtime: Any, answer_mode: str = "single-shot") -> None:
        self._runtime = runtime
        # Preserve long_horizon_memory snapshot optimization on mini/OODA paths.
        self._agent = getattr(runtime, "_learning_agent", runtime)
        self._answer_mode = answer_mode

    def _span_attributes(self, **extra: Any) -> dict[str, Any]:
        attributes: dict[str, Any] = {
            "amplihack.runtime.class": type(self._runtime).__name__,
            "amplihack.answer_mode": self._answer_mode,
        }
        agent_name = getattr(self._runtime, "agent_name", None) or getattr(
            self._runtime, "name", None
        )
        if agent_name:
            attributes["amplihack.agent.name"] = agent_name
        attributes.update({key: value for key, value in extra.items() if value is not None})
        return attributes

    def learn_from_content(self, content: str) -> dict[str, Any]:
        with start_span(
            "goal_agent.learn_from_content",
            tracer_name=__name__,
            attributes=self._span_attributes(content_length=len(content)),
        ):
            return s

*[truncated — see source for full prompt]*