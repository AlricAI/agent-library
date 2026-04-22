# Openai Functions

> import json
from json import JSONDecodeError

from langchain_core.agents import AgentAction, AgentActionMessageLog, AgentFinish
from langchain_core.ex

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import json
from json import JSONDecodeError

from langchain_core.agents import AgentAction, AgentActionMessageLog, AgentFinish
from langchain_core.exceptions import OutputParserException
from langchain_core.messages import (
    AIMessage,
    BaseMessage,
)
from langchain_core.outputs import ChatGeneration, Generation
from typing_extensions import override

from langchain_classic.agents.agent import AgentOutputParser


class OpenAIFunctionsAgentOutputParser(AgentOutputParser):
    """Parses a message into agent action/finish.

    Is meant to be used with OpenAI models, as it relies on the specific
    function_call parameter from OpenAI to convey what tools to use.

    If a function_call parameter is passed, then that is used to get
    the tool and tool input.

    If one is not passed, then the AIMessage is assumed to be the final output.
    """

    @property
    def _type(self) -> str:
        return "openai-functions-agent"

    @staticmethod
    def parse_ai_message(message: BaseMessage) -> AgentAction | AgentFinish:
        """Parse an AI message."""
        if not isinstance(message, AIMessage):
            msg = f"Expected an AI message got {type(message)}"
            raise TypeError(msg)

        function_call = message.additional_kwargs.get("function_call", {})

        if function_call:
            function_name = function_call["name"]
            try:
                if len(function_call["arguments"].strip()) == 0:
                    # OpenAI returns an empty string for functions containing no args
                    _tool_input = {}
                else:
                    # otherwise it returns a json object
                    _tool_input = json.loads(function_call["arguments"], strict=False)
            except JSONDecodeError as e:
                msg = (
                    f"Could not parse tool input: {function_call} because "
                    f"the `arguments` is not valid JSON."
                )
                raise OutputParserEx

*[truncated — see source for full prompt]*