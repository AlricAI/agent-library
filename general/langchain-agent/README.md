# Langchain Agent

> """LangChain adapter agent for TraceCore.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""LangChain adapter agent for TraceCore.

Bridges a LangChain AgentExecutor to the TraceCore reset/observe/act interface.
The agent maps observations to a prompt, invokes the LLM once per step, then
parses the output into a valid TraceCore action dict.

Requirements:
    pip install langchain langchain-openai

Environment:
    OPENAI_API_KEY   — required for the default OpenAI model
    TRACECORE_MODEL  — override model (default: gpt-4o-mini)
"""

from __future__ import annotations

import json
import os
import re
from typing import Any


class LangChainAgent:
    """TraceCore-compatible wrapper around a LangChain chat model."""

    def __init__(self, model: str | None = None) -> None:
        self._model_name = model or os.getenv("TRACECORE_MODEL", "gpt-4o-mini")
        self._llm = None
        self._task_spec: dict = {}
        self._history: list[dict] = []
        self.llm_trace: dict[str, Any] | None = None

    def _build_llm(self) -> None:
        from langchain_openai import ChatOpenAI
        self._llm = ChatOpenAI(model=self._model_name, temperature=0)

    def reset(self, task_spec: dict) -> None:
        self._task_spec = task_spec
        self._history = []
        self.llm_trace = None
        if self._llm is None:
            self._build_llm()

    def observe(self, observation: dict) -> None:
        self._history.append(observation)

    def act(self) -> dict:
        obs = self._history[-1] if self._history else {}
        actions = self._task_spec.get("actions") or {}
        if isinstance(actions, dict):
            action_sigs = ", ".join(
                f"{name}({', '.join(args)})" for name, args in actions.items()
            )
        else:
            action_sigs = "submit(answer)"

        sandbox = self._task_spec.get("sandbox") or {}
        fs_roots = sandbox.get("filesystem_roots") or ["/"]
        roots_str = ", ".join(fs_roots)

        system_prompt = (
            f"You are an autonomous agent solving: {self._task_spec.get('desc

*[truncated — see source for full prompt]*