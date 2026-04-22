# Planning Agent

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

import threading
from typing import List, Optional, Dict, Union, Literal
import json
from reactivex import Subject, Observable, disposable, create
from reactivex import operators as ops
from openai import OpenAI, NOT_GIVEN
import time
from dimos.skills.skills import AbstractSkill
from dimos.agents.agent import OpenAIAgent
from dimos.utils.logging_config import setup_logger
from textwrap import dedent
from pydantic import BaseModel, Field

logger = setup_logger("dimos.agents.planning_agent")

# For response validation
class PlanningAgentResponse(BaseModel):
    type: Literal["dialogue", "plan"]
    content: List[str]
    needs_confirmation: bool

class PlanningAgent(OpenAIAgent):
    """Agent that plans and breaks down tasks through dialogue.
    
    This agent specializes in:
    1. Understanding complex tasks through dialogue
    2. Breaking tasks into concrete, executable steps
    3. Refining plans based on user feedback
    4. Streaming individual steps to ExecutionAgents
    
    The agent maintains conversation state and can refine plans until
    the user confirms they are ready to execute.
    """
    
    def __init__(self,
                 dev_name: str = "PlanningAgent",
                 model_name: str = "gpt-4",
                 input_query_stream: Optional[Observable] = None,
                 use_terminal: bool = False,
                 skills: Optional[AbstractSkill] = None):
    

*[truncated — see source for full prompt]*