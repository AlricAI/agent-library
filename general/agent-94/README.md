# Agent

> #!/usr/bin/env python3
"""
Amber Email Agent - Autonomous Task Execution

Uses Claude Agent SDK with Amber's tools for:
- Writing/reading files
- Sear

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
#!/usr/bin/env python3
"""
Amber Email Agent - Autonomous Task Execution

Uses Claude Agent SDK with Amber's tools for:
- Writing/reading files
- Searching the web
- Generating images
- Managing her Supabase memory
- Git operations
- Running shell commands

Supports THINKHARD mode for multi-iteration deep work:
- Generates spec from vague request
- Runs up to 5 iterations
- Checks criteria after each
- Commits and pushes when done

## Permission Tiers

1. **Strangers** (any email not from Bart):
   - Sandboxed to web/public/amber/ for static HTML
   - Can use ZAD API for data persistence (/api/zad/save, /api/zad/load)
   - No access to app routes, migrations, or sensitive code

2. **Bart** (bdecrem@gmail.com):
   - Full access to all tools and Supabase
   - Prefers drawer/ for backend code
   - Prefers web/app/amber/ for web pages
   - Can create migrations, modify any file

Called from the email handler when Bart asks for something or approves a request.
"""

import argparse
import asyncio
import json
import os
import re
import sys
import urllib.request
from datetime import datetime
from typing import Any, Dict, List, Optional

# Import Claude Agent SDK
try:
    from claude_agent_sdk import ClaudeAgentOptions, ClaudeSDKClient
except ImportError as e:
    print(f"Error importing claude-agent-sdk: {e}", file=sys.stderr)
    sys.exit(1)

# Import Amber's tools
try:
    from amber_sdk_tools import amber_server
except ImportError as e:
    print(f"Error importing amber_sdk_tools: {e}", file=sys.stderr)
    sys.exit(1)

# Supabase config for thinkhard loop state
SUPABASE_URL = os.getenv("SUPABASE_URL") or os.getenv("NEXT_PUBLIC_SUPABASE_URL", "")
SUPABASE_KEY = os.getenv("SUPABASE_SERVICE_KEY") or os.getenv("SUPABASE_SERVICE_ROLE_KEY", "")

# Thinkhard constants
MAX_ITERATIONS = 5
AMBER_COLORS = ["#D4A574", "#B8860B", "#0A0908"]

# Deploy wait time - Railway takes ~5-7 minutes to deploy after push
DEPLOY_WAIT_SECONDS = 420  # 7 minutes

# Permission tiers
BART_EMAIL = "b

*[truncated — see source for full prompt]*