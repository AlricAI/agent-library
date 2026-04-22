# MULTI AGENT ARCHITECTURE DESIGN

> ## Status: Design Document (Proposal)

## Date: 2026-02-20

## Branch: feat/integration-eval-loop

---

## 1. The Problem

### Current Architecture: S

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Multi-Agent Internal Architecture for Goal-Seeking Agents

## Status: Design Document (Proposal)

## Date: 2026-02-20

## Branch: feat/integration-eval-loop

---

## 1. The Problem

### Current Architecture: Single Agent Monolith

Today, a generated goal-seeking agent (`GoalSeekingAgent` in `sdk_adapters/base.py`)
is a single agent that handles everything through one LLM session:

```
GoalSeekingAgent (single LLM session)
  |
  +-- 7 learning tools (learn, search, explain, gaps, verify, store, summary)
  +-- 1 system prompt (growing to 400+ lines for L1-L12 coverage)
  +-- 1 agentic loop (PERCEIVE -> REASON -> ACT -> LEARN)
  +-- 1 memory system (Kuzu/SQLite via amplihack-memory-lib)
```

The `LearningAgent` class in `learning_agent.py` is even more complex. Its
`_synthesize_with_llm` method contains specialized instructions for 8+ reasoning
types (temporal, causal, counterfactual, multi-source synthesis, contradiction
resolution, ratio/trend analysis, novel skill, teaching). Each type adds
conditional prompt sections, resulting in a synthesis prompt that can exceed
3000 tokens of instructions alone.

### Specific Bottlenecks

**1. Prompt Overload**

The `_synthesize_with_llm` method builds prompts with up to 12 conditional
instruction blocks. Each block (temporal worksheet, counterfactual rules,
multi-source synthesis rules) competes for the LLM's attention. When multiple
types apply simultaneously (e.g., a temporal+mathematical+multi-source question),
the combined instructions can confuse the LLM, leading to partial compliance.

Evidence from eval results:

- L9 (causal reasoning): 79% median -- the causal/counterfactual instructions
  are interleaved and sometimes conflict
- L10 (counterfactual): Not yet measured, but expected to be low because the
  same prompt handles both causal AND counterfactual, two distinct reasoning modes
- L4 (procedural): 79% median -- procedural reconstruction competes with
  temporal and synthesis instructions

**2. No Parallelism W

*[truncated — see source for full prompt]*