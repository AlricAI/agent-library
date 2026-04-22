# Parallel Doc Qa

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
import json
import re
import time
from typing import Dict, Iterator, List, Optional, Union

import json5

from qwen_agent.agents.assistant import KNOWLEDGE_SNIPPET, Assistant, format_knowledge_to_source_and_content
from qwen_agent.agents.doc_qa.parallel_doc_qa_member import NO_RESPONSE, ParallelDocQAMember
from qwen_agent.agents.doc_qa.parallel_doc_qa_summary import ParallelDocQASummary
from qwen_agent.agents.keygen_strategies import GenKeyword
from qwen_agent.llm.base import BaseChatModel, ModelServiceError
from qwen_agent.llm.schema import DEFAULT_SYSTEM_MESSAGE, USER, Message
from qwen_agent.log import logger
from qwen_agent.tools import BaseTool
from qwen_agent.tools.doc_parser import DocParser
from qwen_agent.tools.simple_doc_parser import PARSER_SUPPORTED_FILE_TYPES
from qwen_agent.utils.parallel_executor import parallel_exec
from qwen_agent.utils.tokenization_qwen import count_tokens
from qwen_agent.utils.utils import (extract_files_from_messages, extract_text_from_message, get_file_type,
                                    print_traceback)

MAX_NO_RESPONSE_RETRY = 4
DEFAULT_NAME = 'Simple Parallel DocQA With RAG Sum Agents'
DEFAULT_DESC = '简易并行后用RAG召回内容，然后回答的Agent'

PARALLEL_CHUNK_SIZE = 1000  # chunk size param for parallel chunk

MAX_RAG_TOKEN_SIZE = 4500
RAG_CHUNK_SIZE = 300


class ParallelDocQA(Assistant):

    def __init__(self,
      

*[truncated — see source for full prompt]*