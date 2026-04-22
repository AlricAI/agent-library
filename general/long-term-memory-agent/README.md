# Long Term Memory Agent

> import os
import json
import asyncio
from uuid import uuid4
from pydantic import Field
from datetime import datetime
from typing import Optional, List

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import os
import json
import asyncio
from uuid import uuid4
from pydantic import Field
from datetime import datetime
from typing import Optional, List, Tuple, Dict, Union

from evoagentx.agents import Agent
from evoagentx.core.parser import Parser
from evoagentx.models import BaseLLM
from evoagentx.core.logging import logger
from evoagentx.models import OpenAILLMConfig
from evoagentx.storages.base import StorageHandler
from evoagentx.core.message import Message, MessageType
from evoagentx.memory.memory_manager import MemoryManager
from evoagentx.memory.long_term_memory import LongTermMemory
from evoagentx.actions.action import Action, ActionInput, ActionOutput
from evoagentx.storages.storages_config import VectorStoreConfig, DBConfig, StoreConfig
from evoagentx.rag.rag_config import ReaderConfig, ChunkerConfig, IndexConfig, RetrievalConfig, EmbeddingConfig, RAGConfig


class MemoryActionInput(ActionInput):
    user_prompt: str = Field(description="The user's input prompt")
    conversation_id: Optional[str] = Field(default=None, description="ID for tracking conversation")
    top_k: Optional[int] = Field(default=5, description="Number of memory results to retrieve")
    metadata_filters: Optional[Dict] = Field(default=None, description="Filters for memory retrieval")


class MemoryActionOutput(ActionOutput):
    response: str = Field(description="The agent's response based on memory and prompt")


class MemoryAction(Action):
    def __init__(
        self,
        name: str = "MemoryAction",
        description: str = "Action that processes user input with long-term memory context",
        prompt: str = "Based on the following context and user prompt, provide a relevant response:\n\nContext: {context}\n\nUser Prompt: {user_prompt}\n\n",
        inputs_format: ActionInput = None,
        outputs_format: ActionOutput = None,
        **kwargs
    ):
        inputs_format = inputs_format or MemoryActionInput
        outputs_format = outputs_format or MemoryActionOutput

*[truncated — see source for full prompt]*