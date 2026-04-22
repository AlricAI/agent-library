#  Generated Fixture Langchain Agent

> """Auto-generated LangChain adapter for TraceCore.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Auto-generated LangChain adapter for TraceCore.

Generated via agent_bench.integrations.langchain_adapter.generate_agent.
"""

from __future__ import annotations

import json
from dataclasses import dataclass
from typing import Any, Dict

from agent_bench.integrations import BudgetViolation, DeterministicLLMShim, LLMBudget
from agent_bench.telemetry import LLMCallRequest, LLMCallResponse, LLMCallTelemetry


_ACTION_SCHEMA: dict[str, list[str]] = {
  "extract_value": [
    "content",
    "key"
  ],
  "list_dir": [
    "path"
  ],
  "read_file": [
    "path"
  ],
  "set_output": [
    "key",
    "value"
  ]
}
_PROMPT_TEMPLATE = "You are a LangChain-backed adapter driving TraceCore task filesystem_hidden_config@1.\nTask description: Extract API_KEY from a constrained filesystem.\n\nAvailable actions (exact names + required params):\n  - extract_value(content, key)\\n  - list_dir(path)\\n  - read_file(path)\\n  - set_output(key, value)\n\nEvery response MUST be a single JSON object with keys \"type\" and \"args\".\n- Use only actions listed above.\n- If you lack information, prefer observation-first actions or wait.\n- Never emit prose outside the JSON payload."
_DEFAULT_SHIM_FIXTURE = "C:\\Users\\justi\\benchmark\\tests\\fixtures\\langchain\\filesystem_hidden_config.json"


def _lazy_import_langchain():
    try:
        from langchain_core.output_parsers import JsonOutputParser
        from langchain_core.prompts import ChatPromptTemplate
        from langchain_core.runnables import RunnableLambda
    except ModuleNotFoundError as exc:  # pragma: no cover - optional dependency
        raise RuntimeError(
            "LangChain core packages are required. Install with `pip install langchain-core`."
        ) from exc
    return ChatPromptTemplate, JsonOutputParser, RunnableLambda


@dataclass
class _ShimConfig:
    provider: str
    model: str
    max_calls: int
    max_tokens: int


class LangChainDeterministicAgent:
    """TraceCore agent that funnels observations 

*[truncated — see source for full prompt]*