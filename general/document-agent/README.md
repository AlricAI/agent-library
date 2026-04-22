# Document Agent

> """
Document Search Agent.

A document Q&A agent that streams its thoughts and progress in real-time,
allowing users to see exactly what it's doing as

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Document Search Agent.

A document Q&A agent that streams its thoughts and progress in real-time,
allowing users to see exactly what it's doing as it searches documents
and synthesizes answers.

This agent extends BaseStreamingAgent with document-specific configuration
and synthesis prompts.
"""

import logging
from typing import List, Optional

from app.agents.base_agent import (
    AgentConfig,
    AgentContext,
    BaseStreamingAgent,
    ExecutionMode,
    PipelineStep,
    ToolStrategy,
)
from app.tools.document_search_tool import DocumentSearchOutput

logger = logging.getLogger(__name__)


# Document-specific synthesis prompt
DOCUMENT_SYNTHESIS_PROMPT = """You are an intelligent document assistant. Given a user's question and document excerpts, create a helpful, accurate answer.

Guidelines:
- Base your answer ONLY on the provided document content
- Start with a direct answer to the question
- Use **bold** for emphasis on key terms
- Use bullet points (- ) for lists
- Always cite your sources with format: (Source: filename, Page X)
- If the documents don't contain the answer, say so clearly
- Never make up information not present in the documents

IMPORTANT: Output clean, well-formatted markdown without extra blank lines."""


class DocumentAgent(BaseStreamingAgent):
    """
    A streaming document search agent that:
    1. Searches through the user's documents
    2. Retrieves relevant content with citations
    3. Synthesizes an answer based on document context
    
    All steps stream their progress to the user in real-time.
    """
    
    def __init__(self):
        config = AgentConfig(
            name="document-agent",
            display_name="Document Assistant",
            instructions=DOCUMENT_SYNTHESIS_PROMPT,
            tools=["document_search"],
            execution_mode=ExecutionMode.RUN_ONCE,
            tool_strategy=ToolStrategy.PREDEFINED_PIPELINE,
        )
        super().__init__(config)
    
    def pipeline_steps(self, query

*[truncated — see source for full prompt]*