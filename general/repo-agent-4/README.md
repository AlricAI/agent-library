# Repo Agent

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
import time
from enum import Enum, auto
from string import Template
from typing import TYPE_CHECKING, List, Optional, Tuple, Union

if TYPE_CHECKING:
    from github.MainClass import Github
from pydantic import BaseModel

from camel.agents import ChatAgent
from camel.agents.chat_agent import StreamingChatAgentResponse
from camel.logger import get_logger
from camel.messages import BaseMessage
from camel.models import BaseModelBackend, ModelFactory
from camel.responses import ChatAgentResponse
from camel.retrievers import VectorRetriever
from camel.types import (
    ModelPlatformType,
    ModelType,
    OpenAIBackendRole,
    RoleType,
)
from camel.utils import track_agent
from camel.utils.chunker import CodeChunker

logger = get_logger(__name__)


class ProcessingMode(Enum):
    FULL_CONTEXT = auto()
    RAG = auto()


class GitHubFile(BaseModel):
    r"""Model to hold GitHub file information.

    Attributes:
        content (str): The content of the GitHub text.
        file_path (str): The path of the file.
        html_url (str): The actual url of the file.
    """

    content: str
    file_path: str
    html_url: str


class RepositoryInfo(BaseModel):
    r"""Model to hold GitHub repository information.

    Attributes:
        repo_name (str): The full name of the reposi

*[truncated — see source for full prompt]*