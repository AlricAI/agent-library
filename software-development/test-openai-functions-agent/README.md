# Test Openai Functions Agent

> from unittest import mock

import pytest
from autochain.agent.message import (
    ChatMessageHistory,
    MessageType,
)
from autochain.agent.openai_

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
from unittest import mock

import pytest
from autochain.agent.message import (
    ChatMessageHistory,
    MessageType,
)
from autochain.agent.openai_functions_agent.openai_functions_agent import (
    OpenAIFunctionsAgent,
)
from autochain.agent.structs import AgentAction, AgentFinish
from autochain.models.chat_openai import ChatOpenAI


@pytest.fixture
def openai_function_calling_fixture():
    with mock.patch(
        "autochain.models.chat_openai.ChatOpenAI.generate_with_retry",
        return_value={
            "choices": [
                {
                    "message": {
                        "role": "assistant",
                        "content": None,
                        "function_call": {
                            "name": "get_current_weather",
                            "arguments": '{\n  "location": "Toronto, Canada",\n  "format": "celsius"\n}',
                        },
                    }
                }
            ],
            "usage": 10,
        },
    ):
        yield


@pytest.fixture
def openai_response_fixture():
    with mock.patch(
        "autochain.models.chat_openai.ChatOpenAI.generate_with_retry",
        return_value={
            "choices": [
                {
                    "message": {
                        "role": "assistant",
                        "content": "Sure, let me get that information for you.",
                    }
                }
            ],
            "usage": 10,
        },
    ):
        yield


@pytest.fixture
def openai_estimate_confidence_fixture():
    with mock.patch(
        "autochain.models.chat_openai.ChatOpenAI.generate_with_retry",
        return_value={
            "choices": [
                {
                    "message": {
                        "role": "assistant",
                        "content": "the confidence is 4.",
                    }
                }
            ],
            "usage": 10,
        },
    ):
        yield


@pytest.fixture
def is_generation

*[truncated — see source for full prompt]*