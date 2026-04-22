# Base Agent

> from __future__ import annotations

from abc import ABC, abstractmethod
from copy import copy as shallow_copy
from hashlib import md5
from pathlib imp

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
from __future__ import annotations

from abc import ABC, abstractmethod
from copy import copy as shallow_copy
from hashlib import md5
from pathlib import Path
import re
from typing import Any, Final, Literal
import uuid

from pydantic import (
    UUID4,
    BaseModel,
    Field,
    PrivateAttr,
    field_validator,
    model_validator,
)
from pydantic_core import PydanticCustomError
from typing_extensions import Self

from crewai.agent.internal.meta import AgentMeta
from crewai.agents.agent_builder.utilities.base_token_process import TokenProcess
from crewai.agents.cache.cache_handler import CacheHandler
from crewai.agents.tools_handler import ToolsHandler
from crewai.knowledge.knowledge import Knowledge
from crewai.knowledge.knowledge_config import KnowledgeConfig
from crewai.knowledge.source.base_knowledge_source import BaseKnowledgeSource
from crewai.knowledge.storage.base_knowledge_storage import BaseKnowledgeStorage
from crewai.mcp.config import MCPServerConfig
from crewai.memory.memory_scope import MemoryScope, MemorySlice
from crewai.memory.unified_memory import Memory
from crewai.rag.embeddings.types import EmbedderConfig
from crewai.security.security_config import SecurityConfig
from crewai.skills.models import Skill
from crewai.tools.base_tool import BaseTool, Tool
from crewai.types.callback import SerializableCallable
from crewai.utilities.config import process_config
from crewai.utilities.i18n import I18N, get_i18n
from crewai.utilities.logger import Logger
from crewai.utilities.rpm_controller import RPMController
from crewai.utilities.string_utils import interpolate_only


_SLUG_RE: Final[re.Pattern[str]] = re.compile(
    r"^(?:crewai-amp:)?[a-zA-Z0-9][a-zA-Z0-9_-]*(?:#[\w-]+)?$"
)


PlatformApp = Literal[
    "asana",
    "box",
    "clickup",
    "github",
    "gmail",
    "google_calendar",
    "google_sheets",
    "hubspot",
    "jira",
    "linear",
    "notion",
    "salesforce",
    "shopify",
    "slack",
    "stripe",
    "zendesk",
]

Platf

*[truncated — see source for full prompt]*