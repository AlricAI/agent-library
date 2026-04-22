---
name: Cerebellum Agent
description: class CerebellumAgent:
    def __init__(self, cfg):
        self.cfg = cfg

    def format(self, plan):
        return {"type": "noop", "plan": plan}
model: claude-sonnet-4-5
---
class CerebellumAgent:
    def __init__(self, cfg):
        self.cfg = cfg

    def format(self, plan):
        return {"type": "noop", "plan": plan}