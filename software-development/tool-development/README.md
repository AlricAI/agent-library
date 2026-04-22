# TOOL DEVELOPMENT

> Complete guide to creating custom tools for CloudCurio agents.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Tool Development Guide

Complete guide to creating custom tools for CloudCurio agents.

## Table of Contents

- [Overview](#overview)
- [Tool Architecture](#tool-architecture)
- [Creating Tools](#creating-tools)
- [Tool Types](#tool-types)
- [Best Practices](#best-practices)
- [Testing Tools](#testing-tools)
- [Tool Registry](#tool-registry)
- [Advanced Patterns](#advanced-patterns)

## Overview

Tools extend agent capabilities by providing reusable functions for specific tasks. CloudCurio supports multiple tool types that can be seamlessly integrated into agents.

### Tool Characteristics

**Good tools are:**
- **Single-purpose**: Do one thing well
- **Composable**: Can be combined with other tools
- **Testable**: Easy to unit test
- **Documented**: Clear inputs and outputs
- **Reliable**: Handle errors gracefully
- **Performant**: Execute efficiently

### Tool Types Supported

- **Python Tools**: Native Python functions
- **Shell Tools**: System commands and scripts
- **MCP Tools**: Model Context Protocol integrations
- **HTTP Tools**: REST API endpoints

## Tool Architecture

### Base Tool Pattern

All tools follow a standardized interface:

```python
from typing import Any, Dict, Optional
from dataclasses import dataclass


@dataclass
class ToolResult:
    """Standardized tool result format."""
    success: bool
    data: Any
    error: Optional[str] = None
    metadata: Optional[Dict[str, Any]] = None


class BaseTool:
    """Base class for all tools."""
    
    # Tool metadata
    name: str = "base_tool"
    description: str = "Base tool class"
    version: str = "1.0.0"
    
    def __init__(self, config: Optional[Dict[str, Any]] = None):
        """Initialize tool with optional configuration."""
        self.config = config or {}
    
    def execute(self, input_data: Any) -> ToolResult:
        """
        Execute the tool with given input.
        
        Args:
            input_data: Input for the tool
            
        Returns:
            ToolRes

*[truncated — see source for full prompt]*