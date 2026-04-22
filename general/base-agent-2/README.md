# Base Agent

> from abc import abstractmethod
import functools
import warnings
import inspect
from typing import (
    Any,
    Callable,
    Dict,
    List,
    Lit

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
from abc import abstractmethod
import functools
import warnings
import inspect
from typing import (
    Any,
    Callable,
    Dict,
    List,
    Literal,
    Sequence,
    Optional,
    Union,
    Type,
    cast,
    overload,
)
from typing_extensions import deprecated

from pydantic._internal._model_construction import ModelMetaclass
from llama_index.core.agent.workflow.prompts import (
    DEFAULT_STATE_PROMPT,
    DEFAULT_EARLY_STOPPING_PROMPT,
)
from llama_index.core.agent.workflow.agent_context import AgentContext
from llama_index.core.agent.workflow.workflow_events import (
    AgentOutput,
    AgentInput,
    AgentSetup,
    AgentStream,
    AgentWorkflowStartEvent,
    AgentStreamStructuredOutput,
    ToolCall,
    ToolCallResult,
)
from llama_index.core.bridge.pydantic import (
    BaseModel,
    Field,
    ConfigDict,
    field_validator,
)
from llama_index.core.prompts import PromptTemplate
from llama_index.core.agent.utils import generate_structured_response
from llama_index.core.llms import ChatMessage, ChatResponse, LLM, TextBlock
from llama_index.core.memory import BaseMemory, ChatMemoryBuffer
from llama_index.core.prompts.base import BasePromptTemplate, PromptTemplate
from llama_index.core.prompts.mixin import PromptMixin, PromptMixinType, PromptDictType
from llama_index.core.tools import (
    BaseTool,
    AsyncBaseTool,
    FunctionTool,
    ToolOutput,
    ToolSelection,
    adapt_to_async_tool,
)
from llama_index.core.workflow import Context
from llama_index.core.objects import ObjectRetriever
from llama_index.core.settings import Settings
from llama_index.core.workflow.context import Context
from llama_index.core.workflow.decorators import step
from llama_index.core.workflow.events import StartEvent, StopEvent
from llama_index.core.workflow.errors import WorkflowRuntimeError
from llama_index.core.workflow.handler import WorkflowHandler
from llama_index.core.workflow.workflow import Workflow, WorkflowMeta

DEFAULT_MAX_ITERATIONS = 20
DEFAULT_A

*[truncated — see source for full prompt]*