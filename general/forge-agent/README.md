# Forge Agent

> import inspect
import logging
from typing import Any, Optional
from uuid import uuid4

from forge.agent.base import BaseAgent, BaseAgentSettings
from 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import inspect
import logging
from typing import Any, Optional
from uuid import uuid4

from forge.agent.base import BaseAgent, BaseAgentSettings
from forge.agent.protocols import (
    AfterExecute,
    CommandProvider,
    DirectiveProvider,
    MessageProvider,
)
from forge.agent_protocol.agent import ProtocolAgent
from forge.agent_protocol.database.db import AgentDB
from forge.agent_protocol.models.task import (
    Step,
    StepRequestBody,
    Task,
    TaskRequestBody,
)
from forge.command.command import Command
from forge.components.archive_handler import ArchiveHandlerComponent
from forge.components.clipboard import ClipboardComponent
from forge.components.data_processor import DataProcessorComponent
from forge.components.http_client import HTTPClientComponent
from forge.components.math_utils import MathUtilsComponent
from forge.components.system.system import SystemComponent
from forge.components.text_utils import TextUtilsComponent
from forge.components.todo import TodoComponent
from forge.config.ai_profile import AIProfile
from forge.file_storage.base import FileStorage
from forge.llm.prompting.schema import ChatPrompt
from forge.llm.prompting.utils import dump_prompt
from forge.llm.providers.schema import AssistantChatMessage, AssistantFunctionCall
from forge.llm.providers.utils import function_specs_from_commands
from forge.models.action import (
    ActionErrorResult,
    ActionProposal,
    ActionResult,
    ActionSuccessResult,
)
from forge.utils.exceptions import AgentException, AgentTerminated

logger = logging.getLogger(__name__)


class ForgeAgent(ProtocolAgent, BaseAgent):
    """
    The goal of the Forge is to take care of the boilerplate code,
    so you can focus on agent design.

    There is a great paper surveying the agent landscape: https://arxiv.org/abs/2308.11432
    Which I would highly recommend reading as it will help you understand the possibilities.

    ForgeAgent provides component support; https://docs.agpt.co/classic/forge/c

*[truncated — see source for full prompt]*