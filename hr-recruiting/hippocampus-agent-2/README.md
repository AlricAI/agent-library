# Hippocampus Agent

> import time
import requests
import numpy as np
from collections import deque

try:
    import chromadb
    CHROMA_AVAILABLE = True
except ImportError:

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import time
import requests
import numpy as np
from collections import deque

try:
    import chromadb
    CHROMA_AVAILABLE = True
except ImportError:
    CHROMA_AVAILABLE = False

class HippocampusAgent:
    def __init__(self, cfg):
        self.cfg = cfg
        self.backend = cfg["models"]["backend"]
        
        # Safe extraction for nested config
        try:
            self.summarizer_model = cfg["models"]["ollama"]["pfc_right"]
        except KeyError:
            self.summarizer_model = "phi3:3.8b"

        # QMD Settings
        try:
            self.qmd_config = cfg.get("layers", {}).get("subconscious", {}).get("regions", {}).get("hippocampus", {}).get("qmd", {})
            self.threshold = self.qmd_config.get("distillation_threshold", 20)
            self.novelty_threshold = self.qmd_config.get("novelty_threshold", 0.8)
        except KeyError:
            self.threshold = 20
            self.novelty_threshold = 0.8
        
        # Memory Stores
        self.episodic_buffer = []  # Short-term raw OODA traces
        self.novelty_scores = []   # Track novelty over time
        self.total_traces = 0       # Count total traces processed
        
        # Rate limiting for novelty
        self.recent_novelty_scores = deque(maxlen=100)  # Track last 100 novelty scores
        self.max_novelty_rate = 0.3  # Max 30% of recent ticks can trigger growth
        self.novelty_decay = 0.95    # Decay factor for repeated similar inputs
        
        # Vector Store Migration to ChromaDB
        if CHROMA_AVAILABLE:
            try:
                db_path = self.qmd_config.get("vector_store", {}).get("path", "~/.aos/memory/vector").replace("~", "/root")
                self.chroma_client = chromadb.PersistentClient(path=db_path)
                self.collection = self.chroma_client.get_or_create_collection(name="qmd_memory")
                self.using_chroma = True
                self.total_traces = self.collection.count()
                print(f"[QMD] Chro

*[truncated — see source for full prompt]*