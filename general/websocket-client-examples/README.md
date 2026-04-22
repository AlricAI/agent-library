# WEBSOCKET CLIENT EXAMPLES

> """
WebSocket Client Examples for ModPorter-AI

This file provides practical examples for connecting to and using
the WebSocket API from various clien

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
WebSocket Client Examples for ModPorter-AI

This file provides practical examples for connecting to and using
the WebSocket API from various client implementations.
"""

# ============================================================================
# 1. Python Client Example
# ============================================================================

import asyncio
import websockets
import json
from typing import Optional

class ConversionProgressClient:
    """WebSocket client for tracking conversion progress."""

    def __init__(self, conversion_id: str, ws_url: str = "ws://localhost:8080"):
        self.conversion_id = conversion_id
        self.ws_url = ws_url
        self.ws: Optional[websockets.WebSocketClientProtocol] = None
        self.connected = False

    async def connect(self):
        """Connect to the WebSocket server."""
        uri = f"{self.ws_url}/api/v1/conversions/{self.conversion_id}/ws"
        try:
            self.ws = await websockets.connect(uri)
            self.connected = True
            print(f"✓ Connected to conversion {self.conversion_id}")
            return True
        except Exception as e:
            print(f"✗ Connection failed: {e}")
            return False

    async def listen(self):
        """Listen for progress updates."""
        if not self.connected or not self.ws:
            print("Not connected!")
            return

        try:
            async for message in self.ws:
                data = json.loads(message)
                self._handle_message(data)
        except websockets.exceptions.ConnectionClosed:
            print("Connection closed")
        except Exception as e:
            print(f"Error listening for messages: {e}")

    def _handle_message(self, data: dict):
        """Handle incoming WebSocket message."""
        msg_type = data.get("type")
        payload = data.get("data", {})

        if msg_type == "connection_established":
            print(f"✓ {payload.get('message')}")
        el

*[truncated — see source for full prompt]*