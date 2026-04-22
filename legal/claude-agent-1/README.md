# Claude Agent

> #
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtai

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Copyright 2025 Dimensional Inc.
#
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

"""Claude agent implementation for the DIMOS agent framework.

This module provides a ClaudeAgent class that implements the LLMAgent interface
for Anthropic's Claude models. It handles conversion between the DIMOS skill format
and Claude's tools format.
"""

from __future__ import annotations

import json
import os
from typing import Any, Dict, List, Optional, Tuple, Union, cast
import logging

import anthropic
from anthropic.types import ContentBlock, MessageParam, ToolUseBlock
from dotenv import load_dotenv
from httpx._transports import base
from pydantic import BaseModel
from reactivex import Observable
from reactivex.disposable import Disposable
from reactivex.scheduler import ThreadPoolScheduler
from reactivex import create

# Local imports
from dimos.agents.agent import LLMAgent
from dimos.agents.memory.base import AbstractAgentSemanticMemory
from dimos.agents.prompt_builder.impl import PromptBuilder
from dimos.skills.skills import AbstractSkill, SkillLibrary
from dimos.stream.frame_processor import FrameProcessor
from dimos.utils.logging_config import setup_logger
from dimos.utils.threadpool import get_scheduler

# Initialize environment variables
load_dotenv()

# Initialize logger for the Claude agent
logger = setup_logger("dimos.agents.claude")

# Response object compatible with LLMAgent
class ResponseMessage:
    def __init__(self, content="", tool_calls=None, thinking_blocks=None):
   

*[truncated — see source for full prompt]*