#  File Surfer

> import json
import os
import traceback
from typing import List, Sequence, Tuple

from autogen_agentchat.agents import BaseChatAgent
from autogen_agent

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import json
import os
import traceback
from typing import List, Sequence, Tuple

from autogen_agentchat.agents import BaseChatAgent
from autogen_agentchat.base import Response
from autogen_agentchat.messages import (
    BaseChatMessage,
    TextMessage,
)
from autogen_agentchat.utils import remove_images
from autogen_core import CancellationToken, Component, ComponentModel, FunctionCall
from autogen_core.models import (
    AssistantMessage,
    ChatCompletionClient,
    LLMMessage,
    SystemMessage,
    UserMessage,
)
from pydantic import BaseModel
from typing_extensions import Self

from ._markdown_file_browser import MarkdownFileBrowser

# from typing_extensions import Annotated
from ._tool_definitions import (
    TOOL_FIND_NEXT,
    TOOL_FIND_ON_PAGE_CTRL_F,
    TOOL_OPEN_PATH,
    TOOL_PAGE_DOWN,
    TOOL_PAGE_UP,
)


class FileSurferConfig(BaseModel):
    """Configuration for FileSurfer agent"""

    name: str
    model_client: ComponentModel
    description: str | None = None


class FileSurfer(BaseChatAgent, Component[FileSurferConfig]):
    """An agent, used by MagenticOne, that acts as a local file previewer. FileSurfer can open and read a variety of common file types, and can navigate the local file hierarchy.

    Installation:

    .. code-block:: bash

        pip install "autogen-ext[file-surfer]"

    Args:
        name (str): The agent's name
        model_client (ChatCompletionClient): The model to use (must be tool-use enabled)
        description (str): The agent's description used by the team. Defaults to DEFAULT_DESCRIPTION
        base_path (str): The base path to use for the file browser. Defaults to the current working directory.

    """

    component_config_schema = FileSurferConfig
    component_provider_override = "autogen_ext.agents.file_surfer.FileSurfer"

    DEFAULT_DESCRIPTION = "An agent that can handle local files."

    DEFAULT_SYSTEM_MESSAGES = [
        SystemMessage(
            content="""
        You are a helpful AI Ass

*[truncated — see source for full prompt]*