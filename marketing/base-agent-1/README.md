# Base Agent

> import uuid
from abc import ABC, abstractmethod
from copy import copy as shallow_copy
from hashlib import md5
from typing import Any, Callable, Dict, 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import uuid
from abc import ABC, abstractmethod
from copy import copy as shallow_copy
from hashlib import md5
from typing import Any, Callable, Dict, List, Optional, TypeVar

from pydantic import (
    UUID4,
    BaseModel,
    Field,
    InstanceOf,
    PrivateAttr,
    field_validator,
    model_validator,
)
from pydantic_core import PydanticCustomError

from crewai.agents.agent_builder.utilities.base_token_process import TokenProcess
from crewai.agents.cache.cache_handler import CacheHandler
from crewai.agents.tools_handler import ToolsHandler
from crewai.knowledge.knowledge import Knowledge
from crewai.knowledge.knowledge_config import KnowledgeConfig
from crewai.knowledge.source.base_knowledge_source import BaseKnowledgeSource
from crewai.security.security_config import SecurityConfig
from crewai.tools.base_tool import BaseTool, Tool
from crewai.utilities import I18N, Logger, RPMController
from crewai.utilities.config import process_config
from crewai.utilities.converter import Converter
from crewai.utilities.string_utils import interpolate_only

T = TypeVar("T", bound="BaseAgent")


class BaseAgent(ABC, BaseModel):
    """Abstract Base Class for all third party agents compatible with CrewAI.

    Attributes:
        id (UUID4): Unique identifier for the agent.
        role (str): Role of the agent.
        goal (str): Objective of the agent.
        backstory (str): Backstory of the agent.
        cache (bool): Whether the agent should use a cache for tool usage.
        config (Optional[Dict[str, Any]]): Configuration for the agent.
        verbose (bool): Verbose mode for the Agent Execution.
        max_rpm (Optional[int]): Maximum number of requests per minute for the agent execution.
        allow_delegation (bool): Allow delegation of tasks to agents.
        tools (Optional[List[Any]]): Tools at the agent's disposal.
        max_iter (int): Maximum iterations for an agent to execute a task.
        agent_executor (InstanceOf): An instance of the CrewAge

*[truncated — see source for full prompt]*