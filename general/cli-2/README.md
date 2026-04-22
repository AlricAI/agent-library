# Cli

> #!/usr/bin/env python3
"""Command-line interface for Semantic Search Agent."""

import asyncio
import sys
import uuid

from agent import search_agent


## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
#!/usr/bin/env python3
"""Command-line interface for Semantic Search Agent."""

import asyncio
import sys
import uuid

from agent import search_agent
from dependencies import AgentDependencies
from pydantic_ai import Agent
from rich.console import Console
from rich.markdown import Markdown
from rich.panel import Panel
from rich.prompt import Prompt

from settings import load_settings

console = Console()


async def stream_agent_interaction(user_input: str, conversation_history: list[str], deps: AgentDependencies) -> tuple[str, str]:
    """Stream agent interaction with real-time tool call display."""

    try:
        # Build context with conversation history
        context = "\n".join(conversation_history[-6:]) if conversation_history else ""

        prompt = f"""Previous conversation:
{context}

User: {user_input}

Search the knowledge base to answer the user's question. Choose the appropriate search strategy (semantic_search or hybrid_search) based on the query type. Provide a comprehensive summary of your findings."""

        # Stream the agent execution
        async with search_agent.iter(prompt, deps=deps) as run:

            response_text = ""

            async for node in run:

                # Handle user prompt node
                if Agent.is_user_prompt_node(node):
                    pass  # Clean start

                # Handle model request node - stream the thinking process
                elif Agent.is_model_request_node(node):
                    # Show assistant prefix at the start
                    console.print("[bold blue]Assistant:[/bold blue] ", end="")

                    # Stream model request events for real-time text
                    async with node.stream(run.ctx) as request_stream:
                        async for event in request_stream:
                            event_type = type(event).__name__

                            if event_type == "PartDeltaEvent":
                                # Extract content from delta

*[truncated — see source for full prompt]*