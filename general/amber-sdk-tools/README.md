# Amber Sdk Tools

> #!/usr/bin/env python3
"""
Amber SDK Tools for Claude Agent SDK

In-process MCP server providing Amber's capabilities:
- Web search
- Image generation

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
#!/usr/bin/env python3
"""
Amber SDK Tools for Claude Agent SDK

In-process MCP server providing Amber's capabilities:
- Web search
- Image generation (fal.ai)
- File operations (via GitHub API when on Railway, local filesystem otherwise)
- Supabase queries (amber_state)
- Git operations (via GitHub API when on Railway)
- Bash commands (restricted)
"""

import base64
import json
import os
import subprocess
import sys
import urllib.request
import urllib.parse
from typing import Any, Dict, Optional

from claude_agent_sdk import create_sdk_mcp_server, tool

# Detect if running on Railway (cloud) vs local
IS_RAILWAY = bool(os.getenv("RAILWAY_ENVIRONMENT") or os.getenv("RAILWAY_SERVICE_NAME"))

# Security: Restrict file operations to codebase (for local mode)
ALLOWED_CODEBASE = os.getenv("AMBER_CODEBASE_PATH", "/Users/bart/Documents/code/vibeceo")

# GitHub config (for Railway mode)
GITHUB_API_TOKEN = os.getenv("GITHUB_API_TOKEN", "")
GITHUB_REPO = os.getenv("GITHUB_REPO", "bdecrem/vibeceo")
GITHUB_BRANCH = os.getenv("GITHUB_BRANCH", "main")

# Supabase config
SUPABASE_URL = os.getenv("SUPABASE_URL") or os.getenv("NEXT_PUBLIC_SUPABASE_URL", "")
SUPABASE_KEY = os.getenv("SUPABASE_SERVICE_KEY") or os.getenv("SUPABASE_SERVICE_ROLE_KEY", "")

# Track files written via GitHub API (for commit batching)
_github_pending_files: Dict[str, str] = {}  # path -> content


def is_safe_path(path: str) -> bool:
    """Ensure path is within allowed codebase."""
    if not path:
        return True
    if path.startswith("/"):
        abs_path = os.path.abspath(path)
    else:
        abs_path = os.path.abspath(os.path.join(ALLOWED_CODEBASE, path))
    return abs_path.startswith(ALLOWED_CODEBASE)


def make_result(text: str, is_error: bool = False) -> Dict[str, Any]:
    """Create MCP tool result in correct format."""
    result = {"content": [{"type": "text", "text": text}]}
    if is_error:
        result["isError"] = True
    return result


# ==========================================

*[truncated — see source for full prompt]*