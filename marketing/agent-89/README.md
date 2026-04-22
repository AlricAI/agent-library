# Agent

> #!/usr/bin/env python3
"""
Creator Incubator Agent

Discovers unique content creator concepts for Twitter/X.
Every 5 minutes: research → ideate → gene

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
#!/usr/bin/env python3
"""
Creator Incubator Agent

Discovers unique content creator concepts for Twitter/X.
Every 5 minutes: research → ideate → generate sample posts → save.

Usage:
    python agent.py              # Run once
    python agent.py --continuous # Run every 5 minutes
    python agent.py --count 10   # Run 10 times then stop
"""

import argparse
import asyncio
import json
import os
import sys
from datetime import datetime
from pathlib import Path
from typing import Optional

# Add parent paths for imports if needed
sys.path.insert(0, str(Path(__file__).parent.parent.parent.parent.parent / "sms-bot"))

try:
    from claude_agent_sdk import ClaudeAgentOptions, ClaudeSDKClient
except ImportError as e:
    print(f"Error: claude-agent-sdk not installed. Run: pip install claude-agent-sdk")
    print(f"Details: {e}")
    sys.exit(1)


class CreatorIncubator:
    """Agent that generates content creator concepts."""

    def __init__(self):
        self.base_dir = Path(__file__).parent
        self.config_path = self.base_dir / "config.json"
        self.task_path = self.base_dir / "task.txt"
        self.output_dir = self.base_dir / "output"
        self.logs_dir = self.base_dir / "logs"

        # Ensure directories exist
        self.output_dir.mkdir(exist_ok=True)
        self.logs_dir.mkdir(exist_ok=True)

        self.config = self._load_config()
        self.task = self._load_task()

    def _load_config(self) -> dict:
        """Load configuration from config.json."""
        if self.config_path.exists():
            with open(self.config_path) as f:
                return json.load(f)
        return {
            "interval_minutes": 5,
            "run_count": 0,
            "last_run": None
        }

    def _save_config(self):
        """Save configuration to config.json."""
        with open(self.config_path, "w") as f:
            json.dump(self.config, f, indent=2)

    def _load_task(self) -> str:
        """Load task instructions from task.txt.

*[truncated — see source for full prompt]*