# Rule Checker Agent

> import json
from pathlib import Path
from datetime import datetime, timezone
import time
from typing import Dict, Any

from omnicoreagent import ToolR

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import json
from pathlib import Path
from datetime import datetime, timezone
import time
from typing import Dict, Any

from omnicoreagent import ToolRegistry, MemoryRouter, OmniCoreAgent, EventRouter
from agents.system_prompts import rule_checker_agent_prompt

# Local tools registry
local_tools = ToolRegistry()

RULES_PATH = Path("agents/data/plan_rules.json")


def load_plan_rules() -> Dict[str, Any]:
    """Load plan rules from disk; return empty structure if missing."""
    if RULES_PATH.exists():
        try:
            with open(RULES_PATH, "r", encoding="utf-8") as f:
                return json.load(f)
        except Exception as e:
            print(f"[RuleChecker] Error loading rules path data: {e}")
            return {}
    return {}


@local_tools.register_tool(
    name="rule_violation_logger",
    description="Log a detected medical claim rule violation to the audit database or report",
    inputSchema={
        "type": "object",
        "properties": {
            "claim_id": {"type": "string"},
            "violation_id": {"type": "string"},
            "rule_id": {"type": "string"},
            "description": {"type": "string"},
            "severity": {"type": "string", "enum": ["low", "medium", "high"]},
            "recommended_action": {"type": "string"},
            "recommended_recovery": {"type": "number"},
        },
        "required": ["claim_id", "violation_id", "rule_id", "description"],
        "additionalProperties": False,
    },
)
async def rule_violation_logger(
    claim_id: str,
    violation_id: str,
    rule_id: str,
    description: str,
    severity: str = "medium",
    recommended_action: str = None,
    recommended_recovery: float = 0.0,
) -> dict:
    """Store or log a single rule violation for later audit synthesis."""
    timestamp = datetime.now(timezone.utc).isoformat()
    violation = {
        "claim_id": claim_id,
        "violation_id": violation_id,
        "rule_id": rule_id,
        "description": description,
 

*[truncated — see source for full prompt]*