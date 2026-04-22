# Scaling Principles

> *Based on research from Hyung Won Chung, Lance Martin, and industry best practices*
*Created: 2025-09-14*

## The Bitter Lesson in AI Engineering

The

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Scaling Principles for OOS Context Engineering

*Based on research from Hyung Won Chung, Lance Martin, and industry best practices*
*Created: 2025-09-14*

## The Bitter Lesson in AI Engineering

The fundamental insight from AI research: **systems that leverage computation and scale with model improvements outperform those that rely on fixed human-designed structure**.

### Core Principle
> Build systems that get better as models get better, not systems that become bottlenecks as models improve.

## Scaling Principles for OOS

### 1. **Leverage Model Capabilities, Don't Replace Them**
- **Good**: Use models for reasoning, planning, and adaptation
- **Bad**: Hard-code logic that models could learn
- **OOS Application**: Let Claude reason about repository patterns vs pre-defining them

### 2. **Scale with Computation, Not Structure**
- **Good**: Systems that can use more compute to get better results
- **Bad**: Fixed pipelines that cap performance regardless of model capability
- **OOS Application**: Dynamic context loading based on available tokens

### 3. **Data-Driven Over Hand-Crafted Rules**
- **Good**: Learn patterns from repository analysis and usage
- **Bad**: Fixed heuristics for command generation
- **OOS Application**: Learn command patterns from user behavior, not pre-define them

### 4. **Composable Over Monolithic**
- **Good**: Modular components that can be recombined
- **Bad**: Single large systems that can't adapt
- **OOS Application**: Independent modules for analysis, generation, execution

## Implementation Strategy

### Context Engineering That Scales

```python
class ScalableContextEngine:
    """Context engine that scales with model capabilities"""

    def __init__(self, model_context_limit: int):
        self.context_limit = model_context_limit
        self.learned_patterns = {}

    def get_context(self, task: str) -> str:
        # Scale context complexity with available capacity
        if self.context_limit > 100k:
            return self

*[truncated — see source for full prompt]*