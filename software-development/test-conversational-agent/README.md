# Test Conversational Agent

> import json
import os
from unittest import mock

import pytest

from autochain.agent.conversational_agent.conversational_agent import (
    Conversati

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import json
import os
from unittest import mock

import pytest

from autochain.agent.conversational_agent.conversational_agent import (
    ConversationalAgent,
)
from autochain.agent.message import (
    ChatMessageHistory,
    MessageType,
)
from autochain.agent.structs import AgentFinish

from autochain.models.chat_openai import ChatOpenAI
from autochain.tools.simple_handoff.tool import HandOffToAgent


@pytest.fixture
def openai_should_answer_fixture():
    with mock.patch(
        "autochain.models.chat_openai.ChatOpenAI.generate_with_retry",
        side_effect=side_effect,
    ):
        yield


def side_effect(*args, **kwargs):
    message = kwargs["messages"][0]["content"]

    if "good" in message:
        return {
            "choices": [
                {
                    "message": {
                        "role": "assistant",
                        "content": "yes, question is resolved",
                    }
                }
            ],
            "usage": 10,
        }
    else:
        return {
            "choices": [
                {
                    "message": {
                        "role": "assistant",
                        "content": "no, question is not resolved",
                    }
                }
            ],
            "usage": 10,
        }


@pytest.fixture
def openai_response_fixture():
    with mock.patch(
        "autochain.models.chat_openai.ChatOpenAI.generate_with_retry",
        return_value={
            "choices": [
                {
                    "message": {
                        "role": "assistant",
                        "content": json.dumps(
                            {
                                "thoughts": {
                                    "plan": "Given workflow policy and previous tools outputs",
                                    "need_use_tool": "Yes if needs to use another tool not used in previous tools outputs else No",
                                },
              

*[truncated — see source for full prompt]*