# Validation Agent

> import uuid
import os
import time
import random

from models.validation import (
    ManifestValidationResult,
    SemanticAnalysisResult,
    Behavio

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ai-engine/src/agents/validation_agent.py
import uuid
import os
import time
import random

from models.validation import (
    ManifestValidationResult,
    SemanticAnalysisResult,
    BehaviorPredictionResult,
    AssetValidationResult,
    ValidationReport as AgentValidationReport,
)


class LLMSemanticAnalyzer:
    def __init__(self, api_key: str = "MOCK_API_KEY"):
        self.api_key = api_key
        if not self.api_key:
            raise ValueError("API key for LLM Semantic Analyzer is required.")
        print("LLMSemanticAnalyzer initialized (mock). API Key: " + self.api_key[:10] + "...")

    def analyze(self, code_snippet: str) -> dict:
        if not code_snippet:
            print("LLMSemanticAnalyzer: No code snippet provided.")
            return {
                "intent_preserved": False,
                "confidence": 0.1,
                "findings": ["No code provided for analysis."],
            }
        print(
            "LLMSemanticAnalyzer: Analyzing code snippet (first 50 chars): '"
            + code_snippet[:50]
            + "...'"
        )
        # Use asyncio.sleep in async context, time.sleep in sync context
        # Since this is called from a synchronous context, we'll keep time.sleep but with a shorter duration
        time.sleep(random.uniform(0.05, 0.1))  # Reduced sleep time
        intent_preserved = True
        confidence = random.uniform(0.75, 0.95)
        findings = []
        if "TODO" in code_snippet or "FIXME" in code_snippet:
            intent_preserved = False
            confidence *= 0.7
            findings.append("Code contains 'TODO'/'FIXME' markers.")
        if "unsafe" in code_snippet.lower() or "danger" in code_snippet.lower():
            confidence *= 0.8
            findings.append("Code contains 'unsafe'/'danger' keywords.")
        if len(code_snippet) < 50 and "simple" not in code_snippet.lower():
            confidence *= 0.9
            findings.append("Code snippet is very short.")
        if "co

*[truncated — see source for full prompt]*