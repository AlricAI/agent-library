#  Openai Assistant Agent

> import asyncio
import json
import logging
import os
from typing import (
    Any,
    AsyncGenerator,
    Awaitable,
    Callable,
    Dict,
    Itera

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import asyncio
import json
import logging
import os
from typing import (
    Any,
    AsyncGenerator,
    Awaitable,
    Callable,
    Dict,
    Iterable,
    List,
    Literal,
    Mapping,
    Optional,
    Sequence,
    Set,
    Union,
    cast,
)

import aiofiles
from autogen_agentchat import EVENT_LOGGER_NAME
from autogen_agentchat.agents import BaseChatAgent
from autogen_agentchat.base import Response
from autogen_agentchat.messages import (
    BaseAgentEvent,
    BaseChatMessage,
    TextMessage,
    ToolCallExecutionEvent,
    ToolCallRequestEvent,
)
from autogen_core import CancellationToken, FunctionCall, Image
from autogen_core.models import ChatCompletionClient, FunctionExecutionResult
from autogen_core.tools import FunctionTool, Tool
from pydantic import BaseModel, Field

from openai import NOT_GIVEN, AsyncAzureOpenAI, AsyncOpenAI, NotGiven
from openai.pagination import AsyncCursorPage
from openai.resources.beta.threads import AsyncMessages, AsyncRuns, AsyncThreads
from openai.types import FileObject
from openai.types.beta import thread_update_params
from openai.types.beta.assistant import Assistant
from openai.types.beta.assistant_response_format_option_param import AssistantResponseFormatOptionParam
from openai.types.beta.assistant_tool_param import AssistantToolParam
from openai.types.beta.code_interpreter_tool_param import CodeInterpreterToolParam
from openai.types.beta.file_search_tool_param import FileSearchToolParam
from openai.types.beta.function_tool_param import FunctionToolParam
from openai.types.beta.thread import Thread, ToolResources, ToolResourcesCodeInterpreter
from openai.types.beta.threads import Message, MessageDeleted, Run
from openai.types.beta.threads.image_url_content_block_param import ImageURLContentBlockParam
from openai.types.beta.threads.image_url_param import ImageURLParam
from openai.types.beta.threads.message_content_part_param import (
    MessageContentPartParam,
)
from openai.types.beta.threads.text_content_block_param

*[truncated — see source for full prompt]*