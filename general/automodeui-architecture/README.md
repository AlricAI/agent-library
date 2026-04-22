# AutoModeUI Architecture

> ## Module: auto_mode_state.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Auto Mode Interactive UI - Architecture Specification

## Module: auto_mode_state.py

### Purpose

Thread-safe shared state container for communication between auto mode execution thread and UI thread.

### Contract

**Inputs**: Updates from auto mode thread (logs, todos, costs, status)
**Outputs**: Snapshots for UI rendering (thread-safe reads)
**Side Effects**: None (pure state container)

### Class: AutoModeState

```python
from dataclasses import dataclass, field
from typing import List, Optional, Dict, Any
from threading import Lock
from enum import Enum
from collections import deque

class ExecutionStatus(Enum):
    INITIALIZING = "initializing"
    RUNNING = "running"
    PAUSED = "paused"
    COMPLETED = "completed"
    ERROR = "error"
    KILLED = "killed"

@dataclass
class TodoItem:
    content: str
    status: str  # "pending", "in_progress", "completed"
    activeForm: str

@dataclass
class SessionInfo:
    session_title: Optional[str] = None
    total_cost: float = 0.0
    message_count: int = 0
    start_time: Optional[float] = None
    current_prompt: Optional[str] = None

class AutoModeState:
    """Thread-safe state container for auto mode execution."""

    def __init__(self, max_log_lines: int = 1000):
        self._lock = Lock()

        # Execution state
        self.status: ExecutionStatus = ExecutionStatus.INITIALIZING
        self.error_message: Optional[str] = None

        # Session info
        self.session_info = SessionInfo()

        # Logs (circular buffer)
        self.logs: deque = deque(maxlen=max_log_lines)

        # Todos
        self.todos: List[TodoItem] = []

        # User commands
        self.pause_requested: bool = False
        self.kill_requested: bool = False
        self.exit_ui_requested: bool = False

    def append_log(self, log_line: str) -> None:
        """Thread-safe log append."""
        with self._lock:
            self.logs.append(log_line)

    def update_todos(self, todos: List[Dict[str, Any]]) -> None:


*[truncated — see source for full prompt]*