# Code Agent

> """CodeAgent - Code generation, execution, review, and refactoring with sandboxing.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""CodeAgent - Code generation, execution, review, and refactoring with sandboxing."""

from dataclasses import dataclass, field, asdict
from typing import Any, Dict, List, Optional, Union
import asyncio
import logging
from praisonaiagents._logging import get_logger

@dataclass
class CodeConfig:
    """Configuration for CodeAgent.
    
    Attributes:
        sandbox: Enable sandboxed execution (default: True for safety)
        timeout: Execution timeout in seconds
        allowed_languages: List of allowed programming languages
        max_output_length: Maximum output length in characters
        working_directory: Working directory for code execution
        environment: Environment variables for execution
    """
    sandbox: bool = True
    timeout: int = 30
    allowed_languages: List[str] = field(default_factory=lambda: ["python"])
    max_output_length: int = 10000
    working_directory: Optional[str] = None
    environment: Dict[str, str] = field(default_factory=dict)
    
    def to_dict(self) -> Dict[str, Any]:
        """Convert config to dictionary."""
        return {k: v for k, v in asdict(self).items() if v is not None}

class CodeAgent:
    """Agent for code generation, execution, review, and refactoring.
    
    This agent provides capabilities for:
    - Generating code from natural language descriptions
    - Executing code in a sandboxed environment
    - Reviewing code for issues and improvements
    - Refactoring and fixing code
    - Explaining code functionality
    
    Example:
        ```python
        from praisonaiagents import CodeAgent
        
        agent = CodeAgent(name="Coder")
        
        # Generate code
        code = agent.generate("Write a function to calculate fibonacci")
        
        # Execute code
        result = agent.execute("print('Hello, World!')")
        
        # Review code
        review = agent.review(code)
        ```
    """
    
    def __init__(
        self,
        name: str = "CodeAgent",
   

*[truncated — see source for full prompt]*