# Context Engineering Architecture

> *Comprehensive architecture design incorporating offloading, reduction, retrieval, isolation, caching, and memory patterns*
*Created: 2025-09-14*

## 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Context Engineering Architecture for OOS

*Comprehensive architecture design incorporating offloading, reduction, retrieval, isolation, caching, and memory patterns*
*Created: 2025-09-14*

## Architecture Overview

The OOS Context Engineering Architecture implements the four core principles: **Write, Select, Compress, Isolate** through a layered, modular design that scales with model improvements.

```
┌─────────────────────────────────────────────────────────────────┐
│                      User Interface Layer                      │
├─────────────────────────────────────────────────────────────────┤
│                  Context Engineering Gateway                   │
│  ┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐   │
│  │   Clarification │ │   Input         │ │   Output        │   │
│  │   Engine        │ │   Processor     │ │   Formatter     │   │
│  └─────────────────┘ └─────────────────┘ └─────────────────┘   │
├─────────────────────────────────────────────────────────────────┤
│                    Context Management Layer                    │
│  ┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐   │
│  │   Memory        │ │   Cache         │ │   Compression   │   │
│  │   Manager       │ │   Manager       │ │   Engine        │   │
│  └─────────────────┘ └─────────────────┘ └─────────────────┘   │
├─────────────────────────────────────────────────────────────────┤
│                    Retrieval Layer                             │
│  ┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐   │
│  │   Hybrid        │ │   Pattern       │ │   Learning      │   │
│  │   Retrieval     │ │   Database      │ │   System        │   │
│  └─────────────────┘ └─────────────────┘ └─────────────────┘   │
├─────────────────────────────────────────────────────────────────┤
│                    Isolation Layer                             │
│  ┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐   │
│  │   Workflow      │ │   Repository    │ │  

*[truncated — see source for full prompt]*