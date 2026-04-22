# Memory Landscape

> Date: 2026-03-17

This document summarizes the memory systems referenced in task `PAP-530` and extracts the design patterns that matter for Paperclip.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Memory Landscape

Date: 2026-03-17

This document summarizes the memory systems referenced in task `PAP-530` and extracts the design patterns that matter for Paperclip.

## What Paperclip Needs From This Survey

Paperclip is not trying to become a single opinionated memory engine. The more useful target is a control-plane memory surface that:

- stays company-scoped
- lets each company choose a default memory provider
- lets specific agents override that default
- keeps provenance back to Paperclip runs, issues, comments, and documents
- records memory-related cost and latency the same way the rest of the control plane records work
- works with plugin-provided providers, not only built-ins

The question is not "which memory project wins?" The question is "what is the smallest Paperclip contract that can sit above several very different memory systems without flattening away the useful differences?"

## Quick Grouping

### Hosted memory APIs

- `mem0`
- `supermemory`
- `Memori`

These optimize for a simple application integration story: send conversation/content plus an identity, then query for relevant memory or user context later.

### Agent-centric memory frameworks / memory OSes

- `MemOS`
- `memU`
- `EverMemOS`
- `OpenViking`

These treat memory as an agent runtime subsystem, not only as a search index. They usually add task memory, profiles, filesystem-style organization, async ingestion, or skill/resource management.

### Local-first memory stores / indexes

- `nuggets`
- `memsearch`

These emphasize local persistence, inspectability, and low operational overhead. They are useful because Paperclip is local-first today and needs at least one zero-config path.

## Per-Project Notes

| Project | Shape | Notable API / model | Strong fit for Paperclip | Main mismatch |
|---|---|---|---|---|
| [nuggets](https://github.com/NeoVertex1/nuggets) | local memory engine + messaging gateway | topic-scoped HRR memory with `remember`, `recall`, `forget`, fact promotion into

*[truncated — see source for full prompt]*