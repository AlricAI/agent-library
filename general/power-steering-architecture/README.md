# Power Steering Architecture

> ## Executive Summary

Power-steering mode is a stop hook enhancement that analyzes session transcripts against 21 considerations to determine if work 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Power-Steering Mode Architecture

## Executive Summary

Power-steering mode is a stop hook enhancement that analyzes session transcripts against 21 considerations to determine if work is truly complete before allowing session termination. It blocks incomplete sessions with actionable continuation prompts and generates comprehensive summaries for completed sessions.

## Design Philosophy

- **Ruthlessly Simple**: Single-purpose module with clear contract
- **Fail-Open**: Never block users due to bugs - always allow stop on errors
- **Zero-BS**: No stubs, no TODOs, every function works or doesn't exist
- **Modular**: Self-contained "brick" that plugs into existing stop hook

## System Architecture

```
┌─────────────────────────────────────────────────┐
│ Claude Code Session Stop Request               │
└────────────────┬────────────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────────────────┐
│ stop.py (Hook Orchestrator)                    │
│                                                 │
│  1. Lock Check                                  │
│  2. Reflection Check                            │
│  3. Power-Steering Check ◄── NEW               │
│  4. Neo4j Cleanup                               │
│                                                 │
└────────────────┬────────────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────────────────┐
│ PowerSteeringChecker Module                    │
│                                                 │
│  Input: transcript_path, session_id            │
│  Output: PowerSteeringResult                    │
│                                                 │
│  Flow:                                          │
│  1. Check if disabled                           │
│  2. Check semaphore (prevent recursion)        │
│  3. Detect Q&A session                          │
│  4. Load transcript                             │
│  5. Analyze against 

*[truncated — see source for full prompt]*