# SCIENCE

> This document covers the cognitive science and research behind floop's design.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Research & Theory

This document covers the cognitive science and research behind floop's design. The spreading activation system isn't a metaphor — it's a direct implementation of memory retrieval models from decades of cognitive science research, adapted for AI agent behavior management.

## Spreading Activation Theory

**Collins & Loftus (1975)** proposed that human semantic memory is organized as a network where concepts are nodes and relationships are edges. When you think of "doctor," activation spreads to related concepts — "hospital," "nurse," "stethoscope" — with strength decreasing over distance. This explains why related concepts come to mind faster (semantic priming) and why context shapes what you remember.

floop applies this directly: behaviors are semantic nodes, and when you're working in a Go test file, activation spreads from "Go" and "testing" seed nodes through the graph, lighting up behaviors about table-driven tests, error handling patterns, and test coverage — while behaviors about Python or documentation stay dormant.

**Key paper:** Collins, A.M. & Loftus, E.F. (1975). A spreading-activation theory of semantic processing. *Psychological Review*, 82(6), 407-428.

## ACT-R Architecture

**John Anderson's ACT-R** (Adaptive Control of Thought—Rational) formalized how memory retrieval works as a computational process. In ACT-R, every memory chunk has a base-level activation that decays over time and receives contextual boosts from the current goal and environment. The chunk with the highest total activation gets retrieved.

floop mirrors this architecture:

| ACT-R Concept | floop Implementation |
|---|---|
| Memory chunks | Behaviors (graph nodes) |
| Base-level activation | ACT-R base-level activation: B_i = ln(n × L^(-d) / (1-d)) |
| Contextual activation | Spreading activation from seed nodes |
| Retrieval threshold | Minimum activation cutoff (epsilon) |
| Partial matching | Fuzzy predicate evaluation on `when` conditions |
| Activation d

*[truncated — see source for full prompt]*