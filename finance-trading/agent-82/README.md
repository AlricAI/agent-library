# Agent

> #!/usr/bin/env python3
"""
Code Agent - Autonomous Codebase Investigation

Uses Claude Agent SDK with file/git tools for deep code analysis.
Supports 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
#!/usr/bin/env python3
"""
Code Agent - Autonomous Codebase Investigation

Uses Claude Agent SDK with file/git tools for deep code analysis.
Supports investigation queries and PR creation with approval flow.
"""

import argparse
import asyncio
import json
import os
import sys
from typing import Any, Dict, List

# Import Claude Agent SDK
try:
    from claude_agent_sdk import ClaudeAgentOptions, ClaudeSDKClient
except ImportError as e:
    print(f"Error importing claude-agent-sdk: {e}", file=sys.stderr)
    sys.exit(1)

# Import code tools (in-process MCP server)
try:
    from code_sdk_tools import code_server
except ImportError as e:
    print(f"Error importing code_sdk_tools: {e}", file=sys.stderr)
    sys.exit(1)


def load_claude_md(codebase_path: str) -> str:
    """Load CLAUDE.md from codebase root for context."""
    claude_md_path = os.path.join(codebase_path, "CLAUDE.md")
    try:
        with open(claude_md_path, "r", encoding="utf-8") as f:
            return f.read()
    except FileNotFoundError:
        return "(No CLAUDE.md found in codebase root)"


def format_history(history: List[Dict[str, str]]) -> str:
    """Format conversation history for context."""
    if not history:
        return "(First investigation)"

    lines = []
    for msg in history[-5:]:  # Last 5 exchanges
        role = msg.get("role", "unknown").upper()
        content = msg.get("content", "")
        # Truncate long messages
        if len(content) > 500:
            content = content[:500] + "..."
        lines.append(f"{role}: {content}")

    return "\n".join(lines)


def extract_text_segments(message: Any) -> List[str]:
    """Extract text-like segments from SDK messages."""
    raw_segments: List[str] = []

    # Common direct attributes
    for attr in ("text", "result_text", "result"):
        value = getattr(message, attr, None)
        if isinstance(value, str):
            raw_segments.append(value)

    # Message content can be a string or list of blocks
    content =

*[truncated — see source for full prompt]*