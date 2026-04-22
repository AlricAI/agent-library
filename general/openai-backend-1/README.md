# Openai Backend

> """
OpenAI-compatible backend.

Works with:
- OpenAI API (GPT-4o, GPT-4o-mini, o1, etc.)
- LM Studio (local, runs at http://localhost:1234/v1)
- vLLM 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
OpenAI-compatible backend.

Works with:
- OpenAI API (GPT-4o, GPT-4o-mini, o1, etc.)
- LM Studio (local, runs at http://localhost:1234/v1)
- vLLM (local, OpenAI-compatible server)
- Any OpenAI-compatible endpoint (Together, Groq, etc.)

Usage::

    # OpenAI API
    llm = OpenAIBackend(model="gpt-4o-mini", api_key="sk-...")

    # LM Studio (local)
    llm = OpenAIBackend(
        model="llama-3.1-8b",
        base_url="http://localhost:1234/v1",
        api_key="lm-studio",  # LM Studio ignores the key
    )

    # vLLM local server
    llm = OpenAIBackend(
        model="Qwen/Qwen2.5-72B-Instruct",
        base_url="http://localhost:8000/v1",
        api_key="dummy",
    )
"""

from __future__ import annotations

import json
import os

from molfun.agents.llm.base import BaseLLM, LLMResponse, ToolCall


class OpenAIBackend(BaseLLM):
    """
    OpenAI-compatible chat completions with tool calling.

    Set ``base_url`` to point at LM Studio, vLLM, or any
    OpenAI-compatible local server.
    """

    def __init__(
        self,
        model: str = "gpt-4o-mini",
        api_key: str | None = None,
        base_url: str | None = None,
        temperature: float = 0.3,
        max_tokens: int = 4096,
    ):
        super().__init__(model=model, temperature=temperature, max_tokens=max_tokens)
        self.api_key = api_key or os.environ.get("OPENAI_API_KEY", "")
        self.base_url = base_url

        try:
            from openai import OpenAI
        except ImportError:
            raise ImportError(
                "openai package required: pip install openai\n"
                "This backend works with OpenAI API, LM Studio, vLLM, etc."
            )
        kwargs = {}
        if self.base_url:
            kwargs["base_url"] = self.base_url
        self._client = OpenAI(api_key=self.api_key, **kwargs)

    def chat(
        self,
        messages: list[dict],
        tools: list[dict] | None = None,
    ) -> LLMResponse:
        kwargs = {
            "mod

*[truncated — see source for full prompt]*