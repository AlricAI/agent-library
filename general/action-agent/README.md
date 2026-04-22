# Action Agent

> import asyncio
import json
from pydantic import create_model, Field
from typing import Optional, Callable, Type, List, Any

from .agent import Agent
f

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import asyncio
import json
from pydantic import create_model, Field
from typing import Optional, Callable, Type, List, Any

from .agent import Agent
from ..core.logging import logger
from ..core.registry import MODULE_REGISTRY, ACTION_FUNCTION_REGISTRY
from ..models.model_configs import LLMConfig 
from ..actions.action import Action, ActionOutput, ActionInput
from ..utils.utils import generate_dynamic_class_name, make_parent_folder
from ..core.message import Message, MessageType


class ActionAgent(Agent):
    """
    ActionAgent is a specialized agent that executes a provided function directly without LLM.
    It creates an action that uses the provided function as the execution backbone.
    
    Attributes:
        name (str): The name of the agent.
        description (str): A description of the agent's purpose and capabilities.
        inputs (List[dict]): List of input specifications, where each dict contains:
            - name (str): Name of the input parameter
            - type (str): Type of the input
            - description (str): Description of what the input represents
            - required (bool, optional): Whether this input is required (default: True)
        outputs (List[dict]): List of output specifications, where each dict contains:
            - name (str): Name of the output field
            - type (str): Type of the output
            - description (str): Description of what the output represents
            - required (bool, optional): Whether this output is required (default: True)
        execute_func (Callable): The function to execute the agent.
        async_execute_func (Callable, Optional): Async version of the function. If not provided,
            an async wrapper will be automatically created around execute_func.
        llm_config (LLMConfig, optional): Configuration for the language model (minimal usage).
    """
    
    
    def __init__(
        self,
        name: str,
        description: str,
        inputs: List[dict],

*[truncated — see source for full prompt]*