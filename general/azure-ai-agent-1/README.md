#  Azure Ai Agent

> import asyncio
import json
import logging
import os
from typing import (
    Any,
    AsyncGenerator,
    Dict,
    Iterable,
    List,
    Mapping,
 

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
    Dict,
    Iterable,
    List,
    Mapping,
    Optional,
    Sequence,
    Set,
    cast,
)

from autogen_agentchat import TRACE_LOGGER_NAME
from autogen_agentchat.agents import BaseChatAgent
from autogen_agentchat.base import Response
from autogen_agentchat.messages import (
    AgentEvent,
    BaseChatMessage,
    ChatMessage,
    HandoffMessage,
    MultiModalMessage,
    StopMessage,
    TextMessage,
    ToolCallExecutionEvent,
    ToolCallRequestEvent,
)
from autogen_core import CancellationToken, FunctionCall
from autogen_core.models._types import FunctionExecutionResult
from autogen_core.tools import FunctionTool, Tool

from azure.ai.agents.models import (
    Agent,
    AgentsResponseFormat,
    AgentThread,
    AzureAISearchToolDefinition,
    AzureFunctionToolDefinition,
    BingGroundingToolDefinition,
    CodeInterpreterToolDefinition,
    CodeInterpreterToolResource,
    FileInfo,
    FilePurpose,
    FileSearchToolDefinition,
    FileSearchToolResource,
    FileState,
    FunctionDefinition,
    FunctionToolDefinition,
    ListSortOrder,
    MessageRole,
    MessageTextUrlCitationAnnotation,
    RunStatus,
    ThreadRun,
    ToolDefinition,
    ToolOutput,
    ToolResources,
    VectorStore,
    VectorStoreChunkingStrategyRequest,
    VectorStoreDataSource,
    VectorStoreExpirationPolicy,
)
from azure.ai.agents.models._patch import ThreadMessage
from azure.ai.projects.aio import AIProjectClient

from ._types import AzureAIAgentState, ListToolType

trace_logger = logging.getLogger(TRACE_LOGGER_NAME)


class AzureAIAgent(BaseChatAgent):
    """
    Azure AI Assistant agent for AutoGen.

    Installation:

    .. code-block:: bash

        pip install "autogen-ext[azure]"  # For Azure AI Foundry Agent Service

    This agent leverages the Azure AI Assistant API to create AI assistants with capabilities like:

    * Code interpretation and execution
 

*[truncated — see source for full prompt]*