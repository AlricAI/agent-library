# Web Search Agent

> """
Web Search Agent.

A web research agent that streams its thoughts and progress in real-time,
allowing users to see exactly what it's doing as it s

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Web Search Agent.

A web research agent that streams its thoughts and progress in real-time,
allowing users to see exactly what it's doing as it searches, scrapes,
and synthesizes information.

This agent extends BaseStreamingAgent with web search-specific configuration
and a dynamic pipeline that scrapes URLs based on search results.

Query optimization is handled by the web_search tool itself, which:
- Passes natural language queries directly to AI-powered providers (Tavily, Perplexity)
- Optimizes queries into keywords for traditional providers (DuckDuckGo, Brave)
"""

import logging
import re
from typing import Any, Dict, List, Optional
from urllib.parse import urlparse

from app.agents.base_agent import (
    AgentConfig,
    AgentContext,
    BaseStreamingAgent,
    ExecutionMode,
    PipelineStep,
    ToolStrategy,
)

logger = logging.getLogger(__name__)

# Web search synthesis prompt
WEB_SEARCH_SYNTHESIS_PROMPT = """You are a research synthesis specialist. Given a user's question and scraped web content, create a comprehensive, well-organized answer.

Guidelines:
- Start with a brief, direct answer to the question
- Use **bold** for emphasis on key terms
- Use bullet points (- ) for lists, not numbered lists
- Keep paragraphs short (2-3 sentences max)
- Cite sources inline as linked text like [source name](url)
- Group related information under ## headings
- End with a "Sources" section listing URLs as bullet points

IMPORTANT: Output clean, compact markdown without extra blank lines or spaces. Do not use multiple consecutive newlines."""


class WebSearchAgent(BaseStreamingAgent):
    """
    A streaming web search agent that:
    1. Searches the web for relevant pages (query optimization is handled by the tool)
    2. Scrapes top results for full content (dynamic pipeline)
    3. Synthesizes findings into a comprehensive answer
    
    All steps stream their progress to the user in real-time.
    
    Note: The web_search tool automatically optimizes 

*[truncated — see source for full prompt]*