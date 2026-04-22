# Agent

> #!/usr/bin/env python3
"""
Stage 2: Curate top papers and generate daily report

This script uses Claude Agent SDK to analyze all papers fetched in St

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
#!/usr/bin/env python3
"""
Stage 2: Curate top papers and generate daily report

This script uses Claude Agent SDK to analyze all papers fetched in Stage 1,
select the top 5-10 most significant papers, and generate a curated markdown report.

Input: JSON file from fetch_papers.py
Output: Markdown report + JSON with featured paper IDs
"""

import argparse
import asyncio
import json
from datetime import datetime
from pathlib import Path

from claude_agent_sdk import ClaudeAgentOptions, query


CURATION_PROMPT_TEMPLATE = """
You are an AI research analyst tasked with curating the most significant AI/ML papers from arXiv.

You have been provided with ALL papers published today across these categories:
- cs.AI (Artificial Intelligence)
- cs.LG (Machine Learning)
- cs.CV (Computer Vision)
- cs.CL (Computation and Language/NLP)
- stat.ML (Statistics - Machine Learning)

**YOUR TASK:**

1. Read the JSON file at: {input_json_path}

2. Analyze each paper against these curation criteria:
   - **Novelty (30%)**: Is this a new technique/approach or incremental improvement?
   - **Impact Potential (25%)**: Does it have practical applications? Broad applicability?
   - **Author Notability (20%)**: Consider the author_data provided (if available)
   - **Research Quality (15%)**: Rigor, experimental design, results quality
   - **Timeliness (10%)**: Does it address current hot topics or challenges?

3. Select the TOP 5-10 most significant papers. Aim for 7 papers if possible.

4. For each selected paper, write a brief explanation of WHY it was selected.

5. Generate a curated markdown report using the structure below.

6. Use the Write tool to save TWO files:
   a) The markdown report to: {output_md_path}
   b) A JSON file with featured paper metadata to: {output_json_path}

**MARKDOWN REPORT STRUCTURE:**

```markdown
# AI Research Papers - Daily Curated Brief
**Date:** {date_str}
**Curated:** [N] papers from [TOTAL] total submissions

---

## Executive Summary

[Write 2-3 sentences

*[truncated — see source for full prompt]*