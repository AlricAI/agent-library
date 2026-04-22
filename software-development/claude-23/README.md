# CLAUDE

> This file provides guidance to Claude Code (claude.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

OptILLM is an OpenAI API compatible optimizing inference proxy that implements state-of-the-art techniques to improve accuracy and performance of LLMs. It focuses on reasoning improvements for coding, logical, and mathematical queries through inference-time compute optimization.

## Core Architecture

### Main Components

1. **Entry Points**: 
   - `optillm.py` - Main Flask server with inference routing
   - `optillm/inference.py` - Local inference engine with transformer models
   - Setup via `pyproject.toml` with console script `optillm=optillm:main`

2. **Optimization Techniques** (`optillm/`):
   - **Reasoning**: `cot_reflection.py`, `plansearch.py`, `leap.py`, `reread.py` 
   - **Sampling**: `bon.py` (Best of N), `moa.py` (Mixture of Agents), `self_consistency.py`
   - **Search**: `mcts.py` (Monte Carlo Tree Search), `rstar.py` (R* Algorithm)
   - **Verification**: `pvg.py` (Prover-Verifier Game), `z3_solver.py`
   - **Advanced**: `cepo/` (Cerebras Planning & Optimization), `rto.py` (Round Trip)

3. **Decoding Techniques**:
   - `cot_decoding.py` - Chain-of-thought without explicit prompting
   - `entropy_decoding.py` - Adaptive sampling based on token uncertainty
   - `thinkdeeper.py` - Reasoning effort scaling
   - `autothink/` - Query complexity classification with steering vectors

4. **Plugin System** (`optillm/plugins/`):
   - `spl/` - System Prompt Learning (third paradigm learning)
   - `deepthink/` - Gemini-like deep thinking with inference scaling
   - `longcepo/` - Long-context processing with divide-and-conquer
   - `mcp_plugin.py` - Model Context Protocol client
   - `memory_plugin.py` - Short-term memory for unbounded context
   - `privacy_plugin.py` - PII anonymization/deanonymization
   - `executecode_plugin.py` - Code interpreter integration
   - `json_plugin.py` - Structured outputs with outlines library

##

*[truncated — see source for full prompt]*