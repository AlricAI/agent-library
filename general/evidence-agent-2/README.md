# Evidence Agent

> import json
from pathlib import Path
import time
from typing import Dict, Any, List
import re
from omnicoreagent import ToolRegistry, MemoryRouter, Om

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import json
from pathlib import Path
import time
from typing import Dict, Any, List
import re
from omnicoreagent import ToolRegistry, MemoryRouter, OmniCoreAgent, EventRouter
from agents.system_prompts import evidence_agent_prompt

# Local tools registry
local_tools = ToolRegistry()

EVIDENCE_MD_PATH = Path("agents/data/plan_rules.md")


def parse_evidence_snippets(plan_id: str, rule_ids: List[str]) -> List[Dict[str, Any]]:
    """Parse plan_rules.md and extract snippets for given plan + rules."""
    if not EVIDENCE_MD_PATH.exists():
        return [
            {
                "source_id": "MISSING_EVIDENCE_FILE",
                "snippet": "Evidence source file not found.",
                "relevance_score": 0.0,
                "url_status": "unavailable",
            }
        ]

    content = EVIDENCE_MD_PATH.read_text(encoding="utf-8")

    plan_sections = re.split(r"^##\s+(PLAN_[A-Z0-9]+):", content, flags=re.MULTILINE)[
        1:
    ]

    plan_content = ""
    for i in range(0, len(plan_sections), 2):
        pid = plan_sections[i].strip()
        text = plan_sections[i + 1]
        if pid == plan_id:
            plan_content = text
            break

    items = []
    for rule_id in rule_ids:
        pattern = rf"^###\s+({rule_id}):?\s+(.+?)$"
        match = re.search(pattern, plan_content, re.MULTILINE | re.DOTALL)

        if match:
            title = match.group(2).strip()
            start = match.start()
            next_heading = re.search(
                r"\n###\s+[A-Z0-9_]+:", plan_content[start + 1 :], re.MULTILINE
            )
            end = (
                start
                + 1
                + (next_heading.start() if next_heading else len(plan_content))
            )
            full_block = plan_content[start:end].strip()

            source_id_match = re.search(r"\*\*Source ID\*\*:\s+`([^`]+)`", full_block)
            source_id = (
                source_id_match.group(1) if source_id_match else f"{plan_id}_{rule_id}"
  

*[truncated — see source for full prompt]*