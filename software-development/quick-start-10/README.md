# QUICK START

> ## 🚀 What You Get

OOS transforms Claude Code into an intelligent middleware that:
- **Saves you from yourself** with automated context optimization


## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# OOS Context Engineering - Quick Start Guide

## 🚀 What You Get

OOS transforms Claude Code into an intelligent middleware that:
- **Saves you from yourself** with automated context optimization
- **Meta-clarification** - get help from other AIs when Claude asks confusing questions
- **Smart slash commands** - trigger powerful workflows with simple commands
- **Automatic token optimization** - reduce context usage by 40-60%
- **Rambling support** - dump messy thoughts and get organized results

## ⚡ 30-Second Setup

### Step 1: Install as MCP Server
Add to your Claude Code MCP settings:

```json
{
  "mcpServers": {
    "oos-context": {
      "command": "python3",
      "args": ["/home/ubuntu/dev/oos/mcp_server.py"],
      "cwd": "/home/ubuntu/dev/oos"
    }
  }
}
```

### Step 2: Restart Claude Code
The slash commands are now available!

## 🎯 How to Use (User Stories)

### Story 1: "I have a messy idea and need help"
```
You: /brain-dump I want to add authentication but not sure OAuth vs JWT vs sessions, also need database migrations and maybe Redis for caching, also the frontend needs updating
```
**What happens**:
- Auto-analyzes your rambling input
- Optimizes context for token efficiency
- Asks clarifying questions with multiple choice options
- Generates a structured plan with priorities

### Story 2: "Claude's questions are confusing"
```
Claude: "I need clarification on your authentication requirements..."
You: /meta-ai
```
**What happens**:
- Generates a structured prompt optimized for external AI
- You copy/paste to ChatGPT or another Claude instance
- Get better, more detailed answers
- Paste back for optimized implementation

### Story 3: "I want everything auto-optimized"
```
You: /help-me optimize the database performance
```
**What happens**:
- Automatically optimizes context before processing
- Analyzes your codebase for bottlenecks
- Provides specific recommendations
- All within optimized token budget

### Story 4: "I need better documentation"
`

*[truncated — see source for full prompt]*