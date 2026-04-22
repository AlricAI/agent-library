# Prompt Expander Agent

> """
Prompt Expander Agent Module

This module provides the PromptExpanderAgent class for expanding short prompts
into detailed, comprehensive prompts 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Prompt Expander Agent Module

This module provides the PromptExpanderAgent class for expanding short prompts
into detailed, comprehensive prompts for better task execution.

Unlike QueryRewriterAgent (which optimizes queries for search/retrieval),
PromptExpanderAgent focuses on enriching prompts for task execution.

Supported Expansion Strategies:
- **BASIC**: Simple expansion with clarity improvements
- **DETAILED**: Rich expansion with context, constraints, and examples
- **STRUCTURED**: Expansion with clear structure (task, format, requirements)
- **CREATIVE**: Expansion with creative flair and vivid language
- **AUTO**: Automatically selects the best strategy based on prompt analysis

Example:
    from praisonaiagents import PromptExpanderAgent, ExpandStrategy
    
    agent = PromptExpanderAgent()
    
    # Basic expansion
    result = agent.expand("write a movie script in 3 lines")
    print(result.expanded_prompt)
    
    # Detailed expansion
    result = agent.expand("blog about AI", strategy=ExpandStrategy.DETAILED)
    print(result.expanded_prompt)
    
    # With tools for context gathering
    from praisonaiagents.tools import internet_search
    agent = PromptExpanderAgent(tools=[internet_search])
    result = agent.expand("latest AI developments")
"""

import logging
from praisonaiagents._logging import get_logger
from typing import List, Optional, Any, Dict
from dataclasses import dataclass, field
from enum import Enum
from datetime import datetime

class ExpandStrategy(Enum):
    """Enumeration of available prompt expansion strategies."""
    BASIC = "basic"
    DETAILED = "detailed"
    STRUCTURED = "structured"
    CREATIVE = "creative"
    AUTO = "auto"

@dataclass
class ExpandResult:
    """Result of a prompt expansion operation."""
    original_prompt: str
    expanded_prompt: str
    strategy_used: ExpandStrategy
    metadata: Dict[str, Any] = field(default_factory=dict)
    
    def __repr__(self):
        return f"ExpandResult(strategy=

*[truncated — see source for full prompt]*