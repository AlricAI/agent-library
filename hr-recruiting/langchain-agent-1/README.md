# Langchain Agent

> import json
import time
from queue import Queue
from threading import Thread
from typing import Iterator, List, Optional, Union

import langchain_core

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import json
import time
from queue import Queue
from threading import Thread
from typing import Iterator, List, Optional, Union

import langchain_core.messages as lc_msg
from langchain.agents import AgentExecutor, create_structured_chat_agent
from langchain.callbacks.base import BaseCallbackHandler
from langchain.memory import ChatMessageHistory
from langchain.prompts import (ChatPromptTemplate, HumanMessagePromptTemplate,
                               MessagesPlaceholder, PromptTemplate,
                               SystemMessagePromptTemplate)
from langchain_core.agents import AgentAction, AgentFinish
from langchain_openai import ChatOpenAI as _ChatOpenAI
from pydantic import BaseModel

from agentlego.tools import BaseTool
from .. import message_schema as msg
from ..logging import logger
from ..ui import get_translator
from ..utils import parse_inputs, parse_outputs

i18n = get_translator(__file__)

# modified form hub.pull("hwchase17/structured-chat-agent")
STRUCTURED_CHAT_PROMPT = ChatPromptTemplate(
    input_variables=['agent_scratchpad', 'input', 'tool_names', 'tools', 'meta_prompt'],
    input_types={
        'chat_history':
        List[Union[lc_msg.AIMessage, lc_msg.HumanMessage,
                   lc_msg.ChatMessage, lc_msg.SystemMessage,
                   lc_msg.FunctionMessage, lc_msg.ToolMessage]],
    },
    messages=[
        SystemMessagePromptTemplate(
            prompt=PromptTemplate(
                input_variables=['tool_names', 'tools'],
                template=
                'Respond to the human as helpfully and accurately as possible. You have access to the following tools:\n\n{tools}\n\nUse a json blob to specify a tool by providing an action key (tool name) and an action_input key (tool input).\n\nValid "action" values: "Final Answer" or {tool_names}\n\nProvide only ONE action per $JSON_BLOB, as shown:\n\n```\n{{\n  "action": $TOOL_NAME,\n  "action_input": $INPUT\n}}\n```\n\nFollow this format:\n\nQuestion: input question to answer

*[truncated — see source for full prompt]*