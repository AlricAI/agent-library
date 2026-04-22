# Customize Agent

> import json
import inspect
from pydantic import create_model, Field
from typing import Optional, Callable, Type, List, Any, Union, Dict

from .agent i

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import json
import inspect
from pydantic import create_model, Field
from typing import Optional, Callable, Type, List, Any, Union, Dict

from .agent import Agent
from ..core.logging import logger
from ..core.registry import MODULE_REGISTRY, PARSE_FUNCTION_REGISTRY
from ..core.message import Message, MessageType
from ..models.model_configs import LLMConfig 
from ..models.base_model import PARSER_VALID_MODE
from ..prompts.utils import DEFAULT_SYSTEM_PROMPT
from ..prompts.template import PromptTemplate
from ..actions.action import Action, ActionOutput
from ..utils.utils import generate_dynamic_class_name, make_parent_folder
from ..actions.customize_action import CustomizeAction
from ..actions.action import ActionInput
from ..tools.tool import Toolkit, Tool


class CustomizeAgent(Agent):

    """
    CustomizeAgent provides a flexible framework for creating specialized LLM-powered agents without 
    writing custom code. It enables the creation of agents with well-defined inputs and outputs, 
    custom prompt templates, and configurable parsing strategies. 
    
    Attributes:
        name (str): The name of the agent.
        description (str): A description of the agent's purpose and capabilities.
        prompt_template (PromptTemplate, optional): The prompt template that will be used for the agent's primary action. 
        prompt (str, optional): The prompt template that will be used for the agent's primary action.
            Should contain placeholders in the format `{input_name}` for each input parameter.
        llm_config (LLMConfig, optional): Configuration for the language model.
        inputs (List[dict], optional): List of input specifications, where each dict (e.g., `{"name": str, "type": str, "description": str, ["required": bool]}`) contains:
            - name (str): Name of the input parameter
            - type (str): Type of the input
            - description (str): Description of what the input represents
            - required (bool, optional)

*[truncated — see source for full prompt]*