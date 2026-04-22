# Agent

> #!/usr/bin/env python3
"""
KG Query Agent - Claude Agent SDK with In-Process Neo4j Tools

Uses create_sdk_mcp_server to provide Claude with Neo4j quer

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
#!/usr/bin/env python3
"""
KG Query Agent - Claude Agent SDK with In-Process Neo4j Tools

Uses create_sdk_mcp_server to provide Claude with Neo4j query capabilities.
This enables true agentic behavior - Claude iteratively queries until it finds the answer.

Works on Railway (in-process, no external MCP server needed).
"""

import argparse
import asyncio
import json
import os
import sys
from typing import Dict, List, Any

# Import Claude Agent SDK
try:
    from claude_agent_sdk import ClaudeAgentOptions, ClaudeSDKClient
except ImportError as e:
    print(f"Error importing claude-agent-sdk: {e}", file=sys.stderr)
    sys.exit(1)

# Import Neo4j SDK tools (in-process MCP server)
try:
    from neo4j_sdk_tools import neo4j_server
except ImportError as e:
    print(f"Error importing neo4j_sdk_tools: {e}", file=sys.stderr)
    sys.exit(1)


async def run_kg_query(
    user_query: str,
    conversation_history: List[Dict[str, str]],
    todays_report_context: str,
    clean_data_boundary: Dict[str, Any]
) -> str:
    """
    Run KG query using Claude Agent SDK with Neo4j tools.

    Args:
        user_query: User's natural language question
        conversation_history: Previous messages (for follow-ups)
        todays_report_context: Summary of today's arXiv report
        clean_data_boundary: Dict with startDate, endDate, cleanPercentage

    Returns:
        Natural language response (SMS-friendly)
    """
    # Get clean data info
    clean_start = clean_data_boundary.get("startDate", "Unknown")
    clean_end = clean_data_boundary.get("endDate", "Unknown")
    clean_pct = clean_data_boundary.get("cleanPercentage", 0)

    # Format conversation history
    conv_text = ""
    if conversation_history:
        conv_text = "\n".join([
            f"{msg['role'].upper()}: {msg['content']}"
            for msg in conversation_history[-5:]  # Last 5 exchanges
        ])

    # Build prompt - no pre-queried data, Claude uses tools to query
    prompt = f"""You are a Neo4j graph 

*[truncated — see source for full prompt]*