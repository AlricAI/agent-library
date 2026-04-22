# Virtual Memory Agent

> # 
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obta

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Copyright 2023 The Qwen team, Alibaba Group. All rights reserved.
# 
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
# 
#    http://www.apache.org/licenses/LICENSE-2.0
# 
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

import copy
from typing import Dict, Iterator, List, Optional, Union

from qwen_agent.agents.assistant import Assistant
from qwen_agent.llm import BaseChatModel
from qwen_agent.llm.schema import DEFAULT_SYSTEM_MESSAGE, FUNCTION, USER, ContentItem, Message
from qwen_agent.settings import MAX_LLM_CALL_PER_RUN
from qwen_agent.tools import BaseTool

DEFAULT_NAME = 'Virtual Memory Agent'
DEFAULT_DESC = 'This agent can utilize tools to retrieve useful information from external resources or long conversation histories to aid in responding.'


class VirtualMemoryAgent(Assistant):

    def __init__(self,
                 function_list: Optional[List[Union[str, Dict, BaseTool]]] = None,
                 llm: Optional[Union[Dict, BaseChatModel]] = None,
                 system_message: Optional[str] = DEFAULT_SYSTEM_MESSAGE,
                 name: Optional[str] = DEFAULT_NAME,
                 description: Optional[str] = DEFAULT_DESC,
                 files: Optional[List[str]] = None,
                 rag_cfg: Optional[Dict] = None):
        # Add one default retrieval tool
        self.retrieval_tool_name = 'retrieval'
        super().__init__(function_list=[self.retrieval_tool_name] + (function_list or []),
                         llm=llm,
                         system_message=system_message,
                         name=name,
                         description=

*[truncated — see source for full prompt]*