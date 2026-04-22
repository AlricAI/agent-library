# Pfc Agent

> import requests

class PFCAgent:
    def __init__(self, cfg):
        self.cfg = cfg
        self.backend = cfg["models"]["backend"]
        self.olla

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import requests

class PFCAgent:
    def __init__(self, cfg):
        self.cfg = cfg
        self.backend = cfg["models"]["backend"]
        self.ollama_model = cfg["models"]["ollama"]["pfc_left"]
        # Load fallback models from config
        self.fallback_models = cfg["models"].get("fallbacks", [])
        # Parse fallback models (remove "ollama:" prefix)
        self.fallbacks = []
        for fb in self.fallback_models:
            if fb.startswith("ollama:"):
                self.fallbacks.append(fb.replace("ollama:", ""))
            else:
                self.fallbacks.append(fb)

    def _ollama_chat(self, prompt: str, model: str = None) -> str:
        """Call Ollama with fallback support."""
        target_model = model or self.ollama_model
        
        try:
            resp = requests.post(
                "http://localhost:11434/api/generate",
                json={"model": target_model, "prompt": prompt, "stream": False},
                timeout=60,
            )
            resp.raise_for_status()
            return resp.json().get("response", "").strip()
        except Exception as e:
            return f"{{\"raw\": \"error\", \"reason\": \"{str(e)}\"}}"

    def _ollama_chat_with_fallback(self, prompt: str) -> str:
        """Try primary model, then fallbacks if needed."""
        # Try primary model first
        result = self._ollama_chat(prompt, self.ollama_model)
        
        # Check if primary failed
        if '"error"' in result or result.startswith('{"raw": "error"'):
            print(f"[PFC] Primary model {self.ollama_model} failed, trying fallbacks...")
            
            # Try each fallback model
            for fallback_model in self.fallbacks:
                try:
                    print(f"[PFC] Trying fallback: {fallback_model}")
                    fb_result = self._ollama_chat(prompt, fallback_model)
                    
                    # Check if fallback succeeded
                    if '"error"' not in fb_r

*[truncated — see source for full prompt]*