# Video Agent

> """
VideoAgent - A specialized agent class for generating videos using AI models.
This class extends the base Agent class to provide specific function

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
VideoAgent - A specialized agent class for generating videos using AI models.
This class extends the base Agent class to provide specific functionality for video generation,
including support for different video models, sizes, durations, and polling workflow.

Follows the Agent() class patterns:
- Precedence Ladder: Instance > Config > Array > Dict > String > Bool > Default
- Lazy imports for LiteLLM (zero overhead until first use)
- Async-safe with both sync and async methods
- Multi-agent safe (no shared state)
"""
import os
import time
import logging
from praisonaiagents._logging import get_logger
import asyncio
import warnings
from dataclasses import dataclass, field
from typing import Optional, Any, Dict, Union, List, Generator

# Filter out Pydantic warning about fields
warnings.filterwarnings("ignore", "Valid config keys have changed in V2", UserWarning)

# ─────────────────────────────────────────────────────────────────────────────
# VideoConfig - Configuration dataclass following feature_configs.py patterns
# ─────────────────────────────────────────────────────────────────────────────

@dataclass
class VideoConfig:
    """
    Configuration for video generation settings.
    
    Follows the Precedence Ladder pattern:
    - Instance > Config > Array > Dict > String > Bool > Default
    
    Usage:
        # Simple string (model name)
        VideoAgent(llm="openai/sora-2")
        
        # Bool (enable/disable - uses default model)
        VideoAgent(video=True)  # Uses default model
        
        # Dict
        VideoAgent(video={"seconds": "8", "size": "1280x720"})
        
        # Config instance
        VideoAgent(video=VideoConfig(seconds="16", size="720x1280"))
    """
    # Video duration in seconds
    seconds: Optional[str] = "8"
    
    # Video dimensions (e.g., "720x1280", "1280x720")
    size: Optional[str] = None
    
    # Reference image for image-to-video or remix operations
    input_reference: Optional[Any] = None
    
    # T

*[truncated — see source for full prompt]*