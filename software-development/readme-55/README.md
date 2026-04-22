# README

> This directory contains specialized agents that extend Claude Code's capabilities for the amplihack framework.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Amplihack Agents

This directory contains specialized agents that extend Claude Code's capabilities for the amplihack framework.

## Recently Added Agents (2025-10-27)

### Knowledge Work Agents

These agents were ported from amplifier to enhance amplihack's knowledge processing and complexity management capabilities:

#### 1. knowledge-archaeologist

**Value: HIGH** - Traces evolution of knowledge and identifies valuable abandoned approaches
**Location**: `amplihack/specialized/knowledge-archaeologist.md`

- Use when: Understanding concept evolution, paradigm shifts, discovering old solutions for new problems
- Key capability: Temporal analysis of knowledge - how ideas evolve, decay, and resurrect
- Output: Temporal layers, lineage trees, paradigm shifts, decay patterns, revival candidates

#### 2. concept-extractor

**Value: MEDIUM** - Extracts structured knowledge from documents
**Location**: `amplihack/specialized/concept-extractor.md`

- Use when: Processing articles, papers, or documents for knowledge synthesis
- Key capability: Identifies atomic concepts, relationships, tensions, and uncertainties
- Output: Structured JSON with concepts, relationships, tensions, uncertainties

#### 3. insight-synthesizer

**Value: MEDIUM** - Discovers revolutionary connections and breakthrough insights
**Location**: `amplihack/specialized/insight-synthesizer.md`

- Use when: Stuck on complex problems, seeking innovative solutions, need unexpected connections
- Key capability: Collision-zone thinking, pattern-pattern recognition, simplification cascades
- Output: Collision experiments, cross-domain patterns, simplifications, revolutionary insights

## Integration with Amplihack Philosophy

These agents complement amplihack's existing capabilities:

- **knowledge-archaeologist** + **analyzer**: Understand code evolution and why patterns were chosen
- **concept-extractor** + **knowledge-builder**: Enhance documentation and knowledge base creation
- **insight-synthesizer** + **

*[truncated — see source for full prompt]*