# Action Executor

> from __future__ import annotations

"""Action executor with tool registry for goal-seeking agents.

Philosophy:
- Single responsibility: Execute actio

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
from __future__ import annotations

"""Action executor with tool registry for goal-seeking agents.

Philosophy:
- Single responsibility: Execute actions/tools
- Registry pattern for extensibility
- Clear error handling
- Synchronous execution (simpler than async)
"""

from collections.abc import Callable
from dataclasses import dataclass
from typing import Any


@dataclass
class ActionResult:
    """Result of an action execution.

    Attributes:
        success: Whether action succeeded
        output: Output data from the action
        error: Error message if failed
        action_name: Name of the action executed
    """

    success: bool
    output: Any
    error: str | None = None
    action_name: str = ""


class ActionExecutor:
    """Tool registry and executor for goal-seeking agents.

    Provides a registry of available actions (tools) that agents can invoke.
    Each action is a callable that takes parameters and returns a result.

    Philosophy:
    - Simple function-based actions (no complex classes)
    - Clear success/failure reporting
    - Extensible via register_action()

    Example:
        >>> executor = ActionExecutor()
        >>> executor.register_action("greet", lambda name: f"Hello {name}!")
        >>> result = executor.execute("greet", name="Alice")
        >>> print(result.output)  # "Hello Alice!"
    """

    def __init__(self):
        """Initialize action executor with empty registry."""
        self._actions: dict[str, Callable] = {}

    def register_action(self, name: str, func: Callable) -> None:
        """Register an action (tool) with the executor.

        Args:
            name: Action name (must be unique)
            func: Callable that implements the action

        Raises:
            ValueError: If name is empty or already registered

        Example:
            >>> executor = ActionExecutor()
            >>> def add(a: int, b: int) -> int:
            ...     return a + b
            >>> executor.register_action("a

*[truncated — see source for full prompt]*