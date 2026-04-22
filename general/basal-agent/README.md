# Basal Agent

> import numpy as np
import time

class BasalAgent:
    def __init__(self, cfg):
        self.cfg = cfg
        
        # Error tracking for GrowingNN


## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import numpy as np
import time

class BasalAgent:
    def __init__(self, cfg):
        self.cfg = cfg
        
        # Error tracking for GrowingNN
        self.prediction_history = []
        self.error_rate = 0.0
        self.max_history = 100
        
        # GrowingNN Configuration
        self.growing_config = cfg.get("growingnn", {})
        self.node_threshold = self.growing_config.get("add_node_threshold", {"novelty": 0.8, "error": 0.6})
        self.layer_threshold = self.growing_config.get("add_layer_threshold", {"complexity": 0.9})
        
        # Neural Network State
        self.policy_nn = {
            "layers": 3,
            "nodes": [8, 12, 16],
            "activations": [[0.8]*8, [0.5]*12, [0.9]*16],
            "growth_history": []
        }
        
        # Complexity tracking
        self.complexity_scores = []
        
    def execute(self, action, affect):
        """Execute action and track outcomes for error calculation."""
        # Store action for later outcome comparison
        self.last_action = action
        self.last_affect = affect
        
        # Log execution
        print(f"[Basal] Executing: {action.get('type', 'unknown')}")
        
        return {"status": "executed", "action": action}

    def track_error(self, predicted_outcome, actual_outcome):
        """
        Calculate error between predicted and actual outcomes.
        Returns error rate 0.0-1.0.
        """
        if predicted_outcome is None or actual_outcome is None:
            return 0.0
        
        try:
            # Simple error calculation - can be enhanced
            if isinstance(predicted_outcome, (int, float)) and isinstance(actual_outcome, (int, float)):
                error = abs(predicted_outcome - actual_outcome) / max(abs(predicted_outcome), 0.001)
            else:
                # String similarity for non-numeric outcomes
                pred_str = str(predicted_outcome)
                actual_str = str(actual_outcome)
   

*[truncated — see source for full prompt]*