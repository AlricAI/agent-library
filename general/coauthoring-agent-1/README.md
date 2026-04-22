# Coauthoring Agent

> """
CoauthoringAgent - Collaborative storytelling agent.

Inherits from WriterAgent but uses wait_for_user() instead of done()
to enable continuous co

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
CoauthoringAgent - Collaborative storytelling agent.

Inherits from WriterAgent but uses wait_for_user() instead of done()
to enable continuous collaboration with the user.
"""
import sys
import logging
from pathlib import Path

logger = logging.getLogger(__name__)

# Add parent to path for imports
sys.path.append(str(Path(__file__).parent.parent))

from agents.writer_agent import WriterAgent
from tools.interactive import wait_for_user, get_session_state, WaitingForInput
from agents.prompts.loader import build_agent_prompt
import litellm


class CoauthoringAgent(WriterAgent):
    """
    Agent specialized in collaborative storytelling with users.
    
    Inherits all WriterAgent capabilities but replaces the done() tool
    with wait_for_user() to enable continuous collaboration.
    """
    
    def __init__(
        self,
        model: str = "claude-haiku-4-5-20251001",
        story_file: str = "stories/coauthoring_story.md",
        system_prompt: str = None,
        memory: dict = None,
        stream: bool = True,
        agent_id: str = None,
        agent_config: dict = None
    ):
        """
        Initialize CoauthoringAgent.
        
        Args:
            model: LLM model to use
            story_file: Default story file for coauthoring (default: "stories/coauthoring_story.md")
            system_prompt: Optional custom system prompt (defaults to coauthoring prompt)
            memory: Optional initial memory dict
            stream: Whether to stream responses
            agent_id: Optional agent ID for updating config when renaming story
            agent_config: Optional agent configuration dict (for future state persistence)
        """
        # Override system prompt before calling super().__init__
        if system_prompt is None:
            base_prompt = build_agent_prompt("coauthoring", include_tools=True)
            # Add story file context
            system_prompt = f"""{base_prompt}

---

## Your Story File

**Your designated ou

*[truncated — see source for full prompt]*