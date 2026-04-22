# Streaming Agent

> """
Base class for streaming-aware agents.

Provides a framework for agents that can stream their thoughts and progress
directly to the user in real-t

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Base class for streaming-aware agents.

Provides a framework for agents that can stream their thoughts and progress
directly to the user in real-time.
"""

import asyncio
from abc import ABC, abstractmethod
from typing import Awaitable, Callable, Optional

from app.schemas.streaming import StreamEvent, thought, content, error


# Type alias for the streaming callback
StreamCallback = Callable[[StreamEvent], Awaitable[None]]


class StreamingAgent(ABC):
    """
    Base class for agents that stream thoughts to the user.
    
    Subclasses implement run_with_streaming() to execute their logic
    while streaming progress updates via the provided callback.
    """
    
    # Override in subclass
    name: str = "Agent"
    
    @abstractmethod
    async def run_with_streaming(
        self,
        query: str,
        stream: StreamCallback,
        cancel: asyncio.Event,
        context: Optional[dict] = None,
    ) -> str:
        """
        Execute agent logic, streaming thoughts as we go.
        
        Args:
            query: The user's query to process
            stream: Async callback to stream events to the user
            cancel: Event that signals cancellation request
            context: Optional context from dispatcher (conversation history, etc.)
            
        Returns:
            Final output string (also streamed via 'content' events)
        """
        pass
    
    async def stream_thought(self, stream: StreamCallback, message: str, data: dict = None) -> None:
        """Helper to stream a thought event."""
        await stream(thought(source=self.name, message=message, data=data))
    
    async def stream_content(self, stream: StreamCallback, message: str, data: dict = None) -> None:
        """Helper to stream content to the chat message."""
        await stream(content(source=self.name, message=message, data=data))
    
    async def stream_error(self, stream: StreamCallback, message: str, data: dict = None) -> None:
        """H

*[truncated — see source for full prompt]*