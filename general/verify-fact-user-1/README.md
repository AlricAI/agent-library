# Verify Fact User

> Verify this fact against the stored knowledge:

Fact to verify: {{fact}}

Stored knowledge:
{{facts_text}}

Is the fact consistent with stored knowled

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Verify Fact User Prompt

Verify this fact against the stored knowledge:

Fact to verify: {{fact}}

Stored knowledge:
{{facts_text}}

Is the fact consistent with stored knowledge? Return ONLY a JSON object:
{"verified": true/false, "confidence": 0.8, "supporting": ["fact1"], "contradicting": ["fact2"], "reasoning": "explanation"}