# Test Code Act Agent

> import pytest
from unittest.mock import AsyncMock, MagicMock
from typing import Any, Sequence


from llama_index.core.agent.workflow import SimpleAgen

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import pytest
from unittest.mock import AsyncMock, MagicMock
from typing import Any, Sequence


from llama_index.core.agent.workflow import SimpleAgentContext
from llama_index.core.agent.workflow.codeact_agent import CodeActAgent
from llama_index.core.agent.workflow.workflow_events import AgentOutput, ToolCallResult
from llama_index.core.base.llms.types import ChatResponse
from llama_index.core.llms import ChatMessage, LLMMetadata
from llama_index.core.llms.function_calling import FunctionCallingLLM
from llama_index.core.llms.mock import MockFunctionCallingLLM
from llama_index.core.tools import ToolOutput
from llama_index.core.memory import BaseMemory


@pytest.fixture()
def mock_llm():
    # Create a mock that inherits from FunctionCallingLLM
    class MockFunctionCallingLLM(FunctionCallingLLM):
        get_tool_calls_from_response: Any = MagicMock(return_value=[])

        def __init__(self) -> None:
            super().__init__()
            self._responses = []

        @property
        def metadata(self) -> LLMMetadata:
            return LLMMetadata(
                is_function_calling_model=True,
            )

        async def astream_chat(self, *args, **kwargs):
            # Return an async generator that yields each response
            async def gen():
                for response in self._responses:
                    yield response

            return gen()

        async def achat(self, *args, **kwargs):
            pass

        def chat(self, *args, **kwargs):
            pass

        def stream_chat(self, *args, **kwargs):
            pass

        def complete(self, *args, **kwargs):
            pass

        async def acomplete(self, *args, **kwargs):
            pass

        def stream_complete(self, *args, **kwargs):
            pass

        async def astream_complete(self, *args, **kwargs):
            pass

        def _prepare_chat_with_tools(self, *args, **kwargs):
            return {}

    return MockFunctionCallingLLM()


@pytest.f

*[truncated — see source for full prompt]*