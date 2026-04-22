# Router Agent

> """
Router Agent that can use different LLM models based on task requirements.

This module extends the base Agent class to support multiple models an

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Router Agent that can use different LLM models based on task requirements.

This module extends the base Agent class to support multiple models and intelligent
model selection based on task characteristics.
"""

import os
import logging
from praisonaiagents._logging import get_logger
from typing import Dict, List, Optional, Any, Union
from .agent import Agent
from ..llm.model_router import ModelRouter
from ..llm import LLM, TokenUsage
from ..trace.protocol import get_default_emitter

logger = get_logger(__name__)

class RouterAgent(Agent):
    """
    An enhanced agent that can dynamically select and use different LLM models
    based on task requirements, optimizing for cost and performance.
    """
    
    def __init__(
        self,
        models: Optional[Union[List[str], Dict[str, Any]]] = None,
        model_router: Optional[ModelRouter] = None,
        routing_strategy: str = "auto",  # "auto", "manual", "cost-optimized", "performance-optimized"
        primary_model: Optional[str] = None,
        fallback_model: Optional[str] = None,
        **kwargs
    ):
        """
        Initialize a RouterAgent.
        
        Args:
            models: List of model names or dict mapping model names to configurations
            model_router: Custom ModelRouter instance for model selection
            routing_strategy: Strategy for model selection
            primary_model: Primary model to use (overrides routing for simple tasks)
            fallback_model: Fallback model if selected model fails
            **kwargs: Additional arguments passed to parent Agent class
        """
        # Initialize model router
        self.model_router = model_router or ModelRouter()
        self.routing_strategy = routing_strategy
        self.fallback_model = fallback_model or os.getenv('OPENAI_MODEL_NAME', 'gpt-4o-mini')
        
        # Process models configuration
        self.available_models = self._process_models_config(models)
        
        # Set primary model 

*[truncated — see source for full prompt]*