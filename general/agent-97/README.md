# Agent

> #!/usr/bin/env python3
"""
Revision Agent - Uses claude-agent-sdk to revise existing Webtoys/apps.

This agent:
1. Receives current HTML and revision 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
#!/usr/bin/env python3
"""
Revision Agent - Uses claude-agent-sdk to revise existing Webtoys/apps.

This agent:
1. Receives current HTML and revision request
2. Uses Claude (Opus or Sonnet) to make the requested changes
3. Returns the complete updated HTML
"""

import argparse
import asyncio
import json
import sys
import os
from pathlib import Path

from claude_agent_sdk import ClaudeAgentOptions, query

PROMPT_TEMPLATE = """You are a web development expert revising an existing app/website.

## APP INFORMATION
- App Slug: {app_slug}
- User: {user_slug}

## USER'S REVISION REQUEST
{revision_request}

## CURRENT HTML CODE
```html
{current_html}
```

## YOUR TASK
1. Carefully analyze the current HTML code
2. Understand exactly what the user wants changed
3. Make the minimal changes needed to fulfill the request
4. Preserve all existing functionality unless explicitly asked to change it
5. Keep the same structure, style patterns, and design aesthetic
6. Only modify what's strictly necessary for the revision

## OUTPUT INSTRUCTIONS
You MUST use the Write tool to save the complete updated HTML to: {output_path}

The file should contain ONLY the complete HTML document - no markdown, no explanations, just the raw HTML starting with <!DOCTYPE html> or <html>.

Important:
- Do NOT include any markdown code fences
- Do NOT include any explanatory text before or after
- Just write the complete, valid HTML file
"""


def build_prompt(
    app_slug: str,
    user_slug: str,
    revision_request: str,
    current_html: str,
    output_path: Path
) -> str:
    return PROMPT_TEMPLATE.format(
        app_slug=app_slug,
        user_slug=user_slug,
        revision_request=revision_request,
        current_html=current_html,
        output_path=str(output_path),
    )


async def run_agent(
    prompt: str,
    output_dir: Path,
    model: str,
    verbose: bool
) -> None:
    options = ClaudeAgentOptions(
        permission_mode='acceptEdits',
        allowed_tools=['Read', 'Write'],

*[truncated — see source for full prompt]*