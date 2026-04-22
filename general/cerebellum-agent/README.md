# Cerebellum Agent

> class CerebellumAgent:
    def __init__(self, cfg):
        self.cfg = cfg

    def format(self, plan):
        return {"type": "noop", "plan": plan}

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
class CerebellumAgent:
    def __init__(self, cfg):
        self.cfg = cfg

    def format(self, plan):
        return {"type": "noop", "plan": plan}