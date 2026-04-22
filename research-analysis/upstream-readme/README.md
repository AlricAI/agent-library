# UPSTREAM README

> An autonomous ML experimentation framework inspired by [Karpathy's autoresearch](https://github.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# AutoResearch

An autonomous ML experimentation framework inspired by [Karpathy's autoresearch](https://github.com/karpathy/autoresearch).

**Repository**: https://github.com/sighthoundinc/sh-autoresearch

An AI agent explores your project, writes the research strategy, proposes one code change
per iteration, runs the experiment, and keeps the change only if the metric improves.
You approve the strategy once before the loop starts. The loop runs until the time budget
expires. You wake up to a better model.

```
Agent explores → Agent writes strategy → Human approves → Agent runs loop → Better model
```

## Core Concepts

| Concept | What it means |
|---------|--------------|
| **Research strategy** (`program.md`) | Agent-written doc (human approves before loop starts): goal, editable files, ranked experiments |
| **Configuration** (`research.env`) | Training command, metric extractor, baseline, time budget |
| **Single editable file(s)** | Agent only touches files listed in `EDITABLE_FILES` |
| **Fixed evaluation** | Metric is always extracted the same way — never changed during the loop |
| **Git ratchet** | `git commit` if metric improves, `git restore` if not — codebase can only get better |
| **Time budget** | Stops after `MAX_HOURS` so you don't wake up to a runaway loop |

## Quickstart

### Option A: Fully automated (recommended)

Copy the scripts into your project, then give the agent a single prompt — it
does everything else.

```bash
git clone https://github.com/sighthoundinc/sh-autoresearch autoresearch
chmod +x autoresearch/scripts/*.sh
./autoresearch/scripts/init.sh 2      # bootstraps branch, stubs, detects TRAIN_CMD
```

Then paste **Prompt 4 (all-in-one)** from the Agent Prompts section below.
The agent explores the project, writes `research.env` and `program.md`, then
**pauses for your approval** before starting any experiments. One thumbs-up
and it runs the loop autonomously from there.

### Option B: Manual setup

```bash
cp research.env.example 

*[truncated — see source for full prompt]*