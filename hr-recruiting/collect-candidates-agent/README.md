# Collect Candidates Agent

> #!/usr/bin/env python3
"""
Recruiting Candidate Collection Agent
Uses claude-agent-sdk to mine channels for REAL candidates matching criteria
"""

imp

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
#!/usr/bin/env python3
"""
Recruiting Candidate Collection Agent
Uses claude-agent-sdk to mine channels for REAL candidates matching criteria
"""

import argparse
import asyncio
import json
import os
from datetime import datetime
from pathlib import Path

from claude_agent_sdk import ClaudeAgentOptions, query

PROMPT_TEMPLATE = """
You are a talent sourcing expert. Mine the provided channels to find 10-15 REAL CANDIDATES.

**YOU HAVE WEB SEARCH ACCESS - USE IT!** Use the WebSearch tool to find actual people.

RECRUITING SPEC: {refined_spec}

APPROVED CHANNELS TO MINE:
{channels_list}

Your task:
1. For EACH channel, use WebSearch to find 2-3 REAL candidates who fit the spec
2. Extract their profile information (name, bio, GitHub, portfolio, social links)
3. Verify the URLs actually exist and lead to real profiles
4. Score each candidate 1-10 on how well they match the spec
5. Return 10-15 best candidates with complete information

CRITICAL STEPS FOR EACH CHANNEL TYPE:

For LinkedIn channels:
- Use WebSearch with the channel's searchQuery
- Find real LinkedIn profiles (/in/ URLs)
- Extract name, headline, experience, education
- Look for GitHub/portfolio links in their profile
- Verify they match location requirement (USA/Canada)

For GitHub channels:
- Use WebSearch with the channel's searchQuery
- Find real GitHub profiles with relevant repos
- Check their README, bio, pinned repos
- Look for contact info or social links
- Verify they have active recent commits

For DEV Community channels:
- Use WebSearch: "site:dev.to {{author}} AI projects"
- Find their author profile and articles
- Extract links to GitHub/portfolio from articles
- Verify they're students or recent grads

For job board channels (YC, HN):
- Search for people commenting/applying to similar roles
- Find their social profiles (Twitter, LinkedIn, GitHub)
- Verify they're looking for opportunities

**ABSOLUTELY CRITICAL - MANDATORY REQUIREMENTS:**
- EVERY candidate MUST have a real profile URL that you

*[truncated — see source for full prompt]*