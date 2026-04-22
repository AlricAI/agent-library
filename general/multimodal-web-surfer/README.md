#  Multimodal Web Surfer

> import asyncio
import base64
import hashlib
import io
import json
import logging
import os
import re
import sys
import time
import traceback
import wa

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import asyncio
import base64
import hashlib
import io
import json
import logging
import os
import re
import sys
import time
import traceback
import warnings
from typing import (
    Any,
    AsyncGenerator,
    Dict,
    List,
    Optional,
    Sequence,
)
from urllib.parse import quote_plus

import aiofiles
import PIL.Image
from autogen_agentchat.agents import BaseChatAgent
from autogen_agentchat.base import Response
from autogen_agentchat.messages import BaseAgentEvent, BaseChatMessage, MultiModalMessage, TextMessage
from autogen_agentchat.utils import content_to_str, remove_images
from autogen_core import EVENT_LOGGER_NAME, CancellationToken, Component, ComponentModel, FunctionCall
from autogen_core import Image as AGImage
from autogen_core.models import (
    AssistantMessage,
    ChatCompletionClient,
    LLMMessage,
    ModelFamily,
    RequestUsage,
    SystemMessage,
    UserMessage,
)
from PIL import Image
from playwright.async_api import BrowserContext, Download, Page, Playwright, async_playwright
from pydantic import BaseModel
from typing_extensions import Self

from ._events import WebSurferEvent
from ._prompts import (
    WEB_SURFER_QA_PROMPT,
    WEB_SURFER_QA_SYSTEM_MESSAGE,
    WEB_SURFER_TOOL_PROMPT_MM,
    WEB_SURFER_TOOL_PROMPT_TEXT,
)
from ._set_of_mark import add_set_of_mark
from ._tool_definitions import (
    TOOL_CLICK,
    TOOL_HISTORY_BACK,
    TOOL_HOVER,
    TOOL_READ_PAGE_AND_ANSWER,
    TOOL_SCROLL_DOWN,
    TOOL_SCROLL_UP,
    TOOL_SLEEP,
    TOOL_SUMMARIZE_PAGE,
    TOOL_TYPE,
    TOOL_VISIT_URL,
    TOOL_WEB_SEARCH,
)
from ._types import InteractiveRegion, UserContent
from .playwright_controller import PlaywrightController

DEFAULT_CONTEXT_SIZE = 128000


class MultimodalWebSurferConfig(BaseModel):
    name: str
    model_client: ComponentModel
    downloads_folder: str | None = None
    description: str | None = None
    debug_dir: str | None = None
    headless: bool = True
    start_page: str | None = "https://www.bing.com/"
    

*[truncated — see source for full prompt]*