---
name: Verify Fact User
description: Verify this fact against the stored knowledge:

Fact to verify: {{fact}}

Stored knowledge:
{{facts_text}}

Is the fact consistent with stored knowled
model: claude-sonnet-4-5
---
# Verify Fact User Prompt

Verify this fact against the stored knowledge:

Fact to verify: {{fact}}

Stored knowledge:
{{facts_text}}

Is the fact consistent with stored knowledge? Return ONLY a JSON object:
{"verified": true/false, "confidence": 0.8, "supporting": ["fact1"], "contradicting": ["fact2"], "reasoning": "explanation"}