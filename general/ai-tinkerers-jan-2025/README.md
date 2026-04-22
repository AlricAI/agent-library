# Ai Tinkerers Jan 2025

> **Date:** January 20, 2025

## Setup Instructions

**Clone and Install:**
```bash
# Clone the repository
git clone https://github.com/evanvolgas/arbit

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Arbiter Presentation - AI Tinkerers
**Date:** January 20, 2025

## Setup Instructions

**Clone and Install:**
```bash
# Clone the repository
git clone https://github.com/evanvolgas/arbiter.git
cd arbiter

# Create virtual environment
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate

# Install dependencies
pip install -e .
```

**Required API Key:**
```bash
export OPENAI_API_KEY=your_key_here
```

**Optional (for provider comparison demos):**
```bash
export ANTHROPIC_API_KEY=your_key_here
export GOOGLE_API_KEY=your_key_here
```

All examples work with just OpenAI. Additional providers only needed for `provider_switching.py` demo.

---

## Basic Evaluation
### `examples/basic_evaluation.py` lines 47-84

```python
from arbiter import evaluate

result = await evaluate(
    output="Paris is the capital of France",
    reference="The capital of France is Paris",
    evaluators=["semantic"],
    model="gpt-4o-mini"
)

print(f"Score: {result.overall_score:.2f}")
print(f"Cost: ${await result.total_llm_cost():.6f}")
print(f"Time: {result.processing_time:.2f}s")
print(f"LLM Calls: {len(result.interactions)}")
```

**Talking points:**
- Automatic cost tracking with real pricing data
- Complete observability of all LLM interactions
- No manual instrumentation required

---

## Debugging Multi-Call Systems
### `examples/debugging_multi_call.py`

```python
# Run a 15-call customer support agent
data = await run_multi_stage_agent(
    "I can't log in to my account, getting authentication error"
)

results = data["results"]  # 15 EvaluationResults

# Show what was tracked
print_interaction_breakdown(results)    # All 15 calls with tokens/latency
await print_cost_analysis(results)      # Cost by stage
print_performance_analysis(results)     # Slowest calls
print_debug_example(results)            # Full prompt/response inspection
```

**Output shows:**
- Call breakdown: All 15 calls across 5 stages with token counts and latency
- Cost analysis: To

*[truncated — see source for full prompt]*