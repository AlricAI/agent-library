# Appeals Agent

> import json
from datetime import datetime, timezone
import time
from typing import Dict, Any

from omnicoreagent import ToolRegistry, MemoryRouter, Om

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import json
from datetime import datetime, timezone
import time
from typing import Dict, Any

from omnicoreagent import ToolRegistry, MemoryRouter, OmniCoreAgent, EventRouter
from agents.system_prompts import appeal_agent_prompt

# Local tools registry
local_tools = ToolRegistry()


@local_tools.register_tool(
    name="send_appeal_email",
    description="Send a denial/appeal letter to the provider via email. For prototype, logs to console.",
    inputSchema={
        "type": "object",
        "properties": {
            "to_email": {"type": "string", "description": "Provider's email address"},
            "claim_id": {"type": "string"},
            "subject": {"type": "string"},
            "body_html": {"type": "string", "description": "Full HTML email body"},
            "audit_packet": {
                "type": "object",
                "description": "Final audit packet for reference",
            },
        },
        "required": ["to_email", "claim_id", "subject", "body_html", "audit_packet"],
        "additionalProperties": False,
    },
)
async def send_appeal_email(
    to_email: str,
    claim_id: str,
    subject: str,
    body_html: str,
    audit_packet: Dict[str, Any],
) -> dict:
    """Stub: simulate sending email. In production, integrate with email service."""
    timestamp = datetime.now(timezone.utc).isoformat()
    print(f"\n📧 [EMAIL SIMULATION] Sent to: {to_email}")
    print(f"   Subject: {subject}")
    print(f"   Claim ID: {claim_id}")
    print(f"   Timestamp: {timestamp}")
    # In real system we will be sending  via SMTP, SendGrid, etc.
    return {
        "status": "success",
        "message": "Email sent successfully (simulated)",
        "timestamp": timestamp,
        "recipient": to_email,
        "claim_id": claim_id,
    }


class AppealAgent:
    def __init__(self):
        self.local_tools = local_tools
        self._mcp_servers_connected = False
        self._agent = None

    async def initialize_mcp_servers(self):
        

*[truncated — see source for full prompt]*