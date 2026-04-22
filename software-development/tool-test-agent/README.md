# Tool Test Agent

> """
ToolTestAgent for rigorous tool testing and bug hunting.

This agent has access to ALL tools (except done) and systematically tests
them to find b

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
ToolTestAgent for rigorous tool testing and bug hunting.

This agent has access to ALL tools (except done) and systematically tests
them to find bugs and edge cases. Reports detailed bug reports via report_issue().
"""
import sys
import os
import toml
import litellm
import logging
from pathlib import Path
from typing import Optional

logger = logging.getLogger(__name__)

# Add parent directory to sys.path for imports
sys.path.append(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))

from base_agent.base_agent import BaseAgent
from tools.search import find_articles, find_images, find_songs, find_files
from tools.files import read_file, edit_file, add_to_story
from tools.articles import read_article, search_articles, list_articles_in_directory
from tools.context import get_context
from tools.interactive import wait_for_user, get_session_state, WaitingForInput
from agents.prompts.loader import build_agent_prompt
from utils.git import ensure_content_branch

# Load config
config = toml.load("config.toml")


class ToolTestAgent(BaseAgent):
    """
    Agent that rigorously tests ALL available tools to hunt down bugs.
    
    This agent has access to every tool in the system (except done) and
    systematically exercises them with various parameters, edge cases, and
    scenarios to find bugs. Uses report_issue() to file detailed bug reports.
    """
    
    def __init__(self, agent_id: Optional[str] = None, **kwargs):
        """Initialize the ToolTestAgent with ALL testing tools.
        
        Args:
            agent_id: Agent ID for identification (optional)
            **kwargs: Additional arguments passed to BaseAgent
        """
        
        # Store agent_id for identification
        self.agent_id = agent_id or "tool-test-agent"
        
        logger.info(f"🧪 ToolTestAgent initialized: id={self.agent_id}")
        
        # Initialize base agent first (to get report_issue)
        system_prompt = build_agent_prompt("tool_test", include_to

*[truncated — see source for full prompt]*