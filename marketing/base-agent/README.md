# Base Agent

> from __future__ import annotations

from abc import ABC, abstractmethod
from collections.abc import Sequence
from copy import copy as shallow_copy
fro

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
from __future__ import annotations

from abc import ABC, abstractmethod
from collections.abc import Sequence
from copy import copy as shallow_copy
from hashlib import md5
from pathlib import Path
import re
from typing import TYPE_CHECKING, Annotated, Any, Final, Literal
import uuid

from pydantic import (
    UUID4,
    BaseModel,
    BeforeValidator,
    Field,
    PrivateAttr,
    SerializeAsAny,
    field_validator,
    model_validator,
)
from pydantic.functional_serializers import PlainSerializer
from pydantic_core import PydanticCustomError
from typing_extensions import Self

from crewai.agent.internal.meta import AgentMeta
from crewai.agents.agent_builder.base_agent_executor import BaseAgentExecutor
from crewai.agents.agent_builder.utilities.base_token_process import TokenProcess
from crewai.agents.cache.cache_handler import CacheHandler
from crewai.agents.tools_handler import ToolsHandler
from crewai.events.base_events import set_emission_counter
from crewai.events.event_bus import crewai_event_bus
from crewai.events.event_context import restore_event_scope, set_last_event_id
from crewai.knowledge.knowledge import Knowledge
from crewai.knowledge.knowledge_config import KnowledgeConfig
from crewai.knowledge.source.base_knowledge_source import BaseKnowledgeSource
from crewai.knowledge.storage.base_knowledge_storage import BaseKnowledgeStorage
from crewai.llms.base_llm import BaseLLM
from crewai.mcp.config import MCPServerConfig
from crewai.memory.memory_scope import MemoryScope, MemorySlice
from crewai.memory.unified_memory import Memory
from crewai.rag.embeddings.types import EmbedderConfig
from crewai.security.security_config import SecurityConfig
from crewai.skills.models import Skill
from crewai.state.checkpoint_config import CheckpointConfig, _coerce_checkpoint
from crewai.tools.base_tool import BaseTool, Tool
from crewai.types.callback import SerializableCallable
from crewai.utilities.config import process_config
from crewai.utilities.logger import Logger

*[truncated — see source for full prompt]*