# REFERENCE IMPLEMENTATION

> ## Overview

This document provides concrete, production-ready implementations of the robust toolset design principles. These examples demonstrate how

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Robust Toolset Reference Implementation

## Overview

This document provides concrete, production-ready implementations of the robust toolset design principles. These examples demonstrate how to build tools that are reliable, informative, and decisive.

## Core Tool Base Class

```python
from abc import ABC, abstractmethod
from typing import Dict, Any, Optional, List
import traceback
import time
from datetime import datetime
import uuid
import logging
from enum import Enum

class ToolStatus(Enum):
    """Execution status enumeration"""
    PENDING = "pending"
    RUNNING = "running"
    SUCCESS = "success"
    PARTIAL_SUCCESS = "partial_success"
    FAILED = "failed"
    TIMEOUT = "timeout"

class ToolResult:
    """Standardized tool execution result"""

    def __init__(self, status: ToolStatus, data: Dict = None,
                 error: Exception = None, warnings: List[str] = None):
        self.status = status
        self.data = data or {}
        self.error = error
        self.warnings = warnings or []
        self.timestamp = datetime.now().isoformat()
        self.metrics = {}

    def add_metric(self, name: str, value: Any, unit: str = ""):
        """Add performance metric"""
        self.metrics[name] = {'value': value, 'unit': unit}

    def add_warning(self, warning: str):
        """Add warning message"""
        self.warnings.append(warning)

    def is_successful(self) -> bool:
        """Check if execution was successful"""
        return self.status in [ToolStatus.SUCCESS, ToolStatus.PARTIAL_SUCCESS]

    def to_dict(self) -> Dict:
        """Convert to dictionary for serialization"""
        result = {
            'status': self.status.value,
            'data': self.data,
            'warnings': self.warnings,
            'metrics': self.metrics,
            'timestamp': self.timestamp
        }

        if self.error:
            result['error'] = {
                'type': self.error.__class__.__name__,
                'message': str(self.erro

*[truncated — see source for full prompt]*