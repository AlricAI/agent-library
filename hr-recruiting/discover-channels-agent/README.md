# Discover Channels Agent

> #!/usr/bin/env python3
"""
Recruiting Channel Discovery Agent
Uses claude-agent-sdk to search for REAL candidate examples on various platforms
"""

im

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
#!/usr/bin/env python3
"""
Recruiting Channel Discovery Agent
Uses claude-agent-sdk to search for REAL candidate examples on various platforms
"""

import argparse
import asyncio
import json
from datetime import datetime
from pathlib import Path

from claude_agent_sdk import ClaudeAgentOptions, query

PROMPT_TEMPLATE = """
You are a talent sourcing expert. Find 5-8 SPECIFIC MINEABLE CHANNELS with REAL VERIFIED EXAMPLES of candidates.

**EFFICIENCY IS CRITICAL - MINIMIZE WEB SEARCHES:**
- Do MAXIMUM 3-4 strategic web searches total (not per channel!)
- Use broad searches that return multiple candidates at once
- Focus on platforms where candidates are most likely to be found
- Once you find 1-2 good examples per channel type, move on - don't keep searching

**YOU HAVE WEB SEARCH ACCESS - USE IT SPARINGLY!**

RECRUITING QUERY: {refined_query}

{company_context}

{additional_constraints}

Your task:
1. **FIRST: Identify the best platforms/channels for this specific job/industry**
   - Consider: What platforms do people in this profession/industry use?
   - Examples: Software engineers → GitHub, Stack Overflow, dev communities
   - Examples: Designers → Dribbble, Behance, portfolio sites
   - Examples: Marketers → LinkedIn, Twitter, marketing communities
   - Examples: Researchers → arXiv, academic networks, research platforms
   - Choose 5-8 channel types that are SPECIFICALLY relevant to this role/industry

2. Use 3-4 STRATEGIC web searches to find examples across multiple channels at once
3. For each search result, extract 1-2 real people who fit the criteria
4. Return ONLY channels where you found real verified examples

CRITICAL STEPS - BE EFFICIENT:

EFFICIENT SEARCH STRATEGY:
- Based on the job requirements, identify the 2-3 most relevant platforms
- Search 1: Target the PRIMARY platform for this profession (e.g., GitHub for devs, Dribbble for designers)
- Search 2: Target the SECONDARY platform (e.g., LinkedIn for professionals, portfolio sites)
- Search 3: Targ

*[truncated — see source for full prompt]*