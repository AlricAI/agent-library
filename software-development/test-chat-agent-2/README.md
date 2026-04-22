# Test Chat Agent

> # Licensed under the Apache License, Version 2.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ========= Copyright 2023-2024 @ CAMEL-AI.org. All Rights Reserved. =========
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
# ========= Copyright 2023-2024 @ CAMEL-AI.org. All Rights Reserved. =========
import asyncio
import json
from copy import deepcopy
from io import BytesIO
from typing import List
from unittest.mock import AsyncMock, MagicMock

import pytest
from openai.types.chat.chat_completion import Choice
from openai.types.chat.chat_completion_message import ChatCompletionMessage
from openai.types.chat.chat_completion_message_function_tool_call import (
    ChatCompletionMessageFunctionToolCall,
    Function,
)
from openai.types.completion_usage import CompletionUsage
from PIL import Image
from pydantic import BaseModel, Field

from camel.agents import ChatAgent
from camel.agents.chat_agent import ToolCallingRecord
from camel.configs import ChatGPTConfig
from camel.generators import SystemMessageGenerator
from camel.memories import MemoryRecord
from camel.messages import BaseMessage
from camel.models import AnthropicModel, ModelFactory, OpenAIModel
from camel.terminators import ResponseWordsTerminator
from camel.toolkits import (
    FunctionTool,
    MathToolkit,
    SearchToolkit,
)
from camel.types import (
    ChatCompletion,
    ModelPlatformType,
    ModelType,
    OpenAIBackendRole,
    RoleType,
    TaskType,
    UnifiedModelType,
)
from camel.utils.async_func import sync_funcs_to_async

model_backend_rsp_base = ChatCompletion(
    id="mock_response_id",
    c

*[truncated — see source for full prompt]*