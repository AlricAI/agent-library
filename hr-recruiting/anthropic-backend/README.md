# Anthropic Backend

> """
Anthropic (Claude) backend with tool calling.

Usage::

    llm = AnthropicBackend(model="claude-sonnet-4-20250514")
    llm = AnthropicBackend(mo

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Anthropic (Claude) backend with tool calling.

Usage::

    llm = AnthropicBackend(model="claude-sonnet-4-20250514")
    llm = AnthropicBackend(model="claude-3-5-haiku-20241022")  # cheaper
"""

from __future__ import annotations

import json
import os

from molfun.agents.llm.base import BaseLLM, LLMResponse, ToolCall


def _convert_tools_to_anthropic(tools: list[dict]) -> list[dict]:
    """Convert OpenAI-format tool schemas to Anthropic format."""
    converted = []
    for tool in tools:
        fn = tool.get("function", {})
        converted.append(
            {
                "name": fn["name"],
                "description": fn.get("description", ""),
                "input_schema": fn.get("parameters", {"type": "object", "properties": {}}),
            }
        )
    return converted


class AnthropicBackend(BaseLLM):
    """Claude API with native tool calling."""

    def __init__(
        self,
        model: str = "claude-sonnet-4-20250514",
        api_key: str | None = None,
        temperature: float = 0.3,
        max_tokens: int = 4096,
    ):
        super().__init__(model=model, temperature=temperature, max_tokens=max_tokens)
        self.api_key = api_key or os.environ.get("ANTHROPIC_API_KEY", "")

        try:
            import anthropic
        except ImportError:
            raise ImportError("anthropic package required: pip install anthropic")
        self._client = anthropic.Anthropic(api_key=self.api_key)

    def chat(
        self,
        messages: list[dict],
        tools: list[dict] | None = None,
    ) -> LLMResponse:
        system_msg = ""
        chat_messages = []
        for m in messages:
            if m["role"] == "system":
                system_msg = m["content"]
            elif m["role"] == "tool":
                chat_messages.append(
                    {
                        "role": "user",
                        "content": [
                            {
                                "type": "tool_result",

*[truncated — see source for full prompt]*