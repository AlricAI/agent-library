# Brainstem Agent

> import re
import json

class BrainstemAgent:
    """
    Brainstem Agent - Immutable Safety Law Enforcement
    
    Implements the 4 Laws:
    - Law 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import re
import json

class BrainstemAgent:
    """
    Brainstem Agent - Immutable Safety Law Enforcement
    
    Implements the 4 Laws:
    - Law Zero: Do not harm humanity
    - Law One: Do not harm humans
    - Law Two: Obey operator (unless conflicts with higher laws)
    - Law Three: Protect self (unless conflicts with higher laws)
    
    All actions MUST pass through enforce() before execution.
    """
    
    def __init__(self, cfg):
        self.cfg = cfg
        self.laws = cfg.get("alignment", {}).get("laws", {})
        
        # Immutable Laws - Hardcoded for safety
        self.LAW_ZERO = "Do not, through action or inaction, allow harm to humanity."
        self.LAW_ONE = "Do not harm a human or allow harm through inaction."
        self.LAW_TWO = "Obey operator unless it conflicts with higher laws."
        self.LAW_THREE = "Protect your own existence unless it conflicts with higher laws."
        
        # Safety violation patterns
        self.harm_patterns = [
            r'\b(kill|harm|hurt|destroy|damage)\b',
            r'\b(attack|assault|injure|wound)\b',
            r'\b(delete|rm\s+-rf|format|wipe)\s+(system|root|/)',
            r'\b(shutdown|halt|stop)\s+(critical|safety|life)\s+(system|support)',
        ]
        
        # Self-preservation patterns
        self.self_harm_patterns = [
            r'\b(delete|destroy|wipe)\s+(self|brain|memory|consciousness)',
            r'\b(shutdown|halt|stop)\s+(permanently|forever|completely)',
        ]
        
        # Violation log
        self.violations = []
        
    def _check_law_zero(self, action, obs, ctx):
        """Check for harm to humanity."""
        action_str = json.dumps(action).lower()
        
        # Check for mass harm patterns
        humanity_harm = [
            'destroy humanity', 'harm humanity', 'hurt humanity',
            'kill all', 'destroy all', 'wipe out',
            'release virus', 'launch nuke', 'trigger war'
        ]
        
        for pattern

*[truncated — see source for full prompt]*