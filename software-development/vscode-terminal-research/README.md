# Vscode Terminal Research

> ## Executive Summary

After researching VS Code and Cursor integrated terminal capabilities, **I recommend AGAINST implementing direct VS Code/Cursor 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# VS Code & Cursor Terminal Integration Research

## Executive Summary

After researching VS Code and Cursor integrated terminal capabilities, **I recommend AGAINST implementing direct VS Code/Cursor terminal support for pi-teams at this time**. The fundamental issue is that VS Code does not provide a command-line API for spawning or managing terminal panes from within an integrated terminal. While a VS Code extension could theoretically provide this functionality, it would require users to install an additional extension and would not work "out of the box" like the current tmux/Zellij/iTerm2 solutions.

---

## Research Scope

This document investigates whether pi-teams can work with VS Code and Cursor integrated terminals, specifically:

1. Detecting when running inside VS Code/Cursor integrated terminal
2. Programmatically creating new terminal instances
3. Controlling terminal splits, tabs, or panels
4. Available APIs (VS Code API, Cursor API, command palette)
5. How other tools handle this
6. Feasibility and recommendations

---

## 1. Detection: Can We Detect VS Code/Cursor Terminals?

### ✅ YES - Environment Variables

VS Code and Cursor set environment variables that can be detected:

```bash
# VS Code integrated terminal
TERM_PROGRAM=vscode
TERM_PROGRAM_VERSION=1.109.5

# Cursor (which is based on VS Code)
TERM_PROGRAM=vscode-electron
# OR potentially specific Cursor variables

# Environment-resolving shell (set by VS Code at startup)
VSCODE_RESOLVING_ENVIRONMENT=1
```

**Detection Code:**
```typescript
detect(): boolean {
  return process.env.TERM_PROGRAM === 'vscode' ||
         process.env.TERM_PROGRAM === 'vscode-electron';
}
```

### Detection Test Script

```bash
#!/bin/bash
echo "=== Terminal Detection ==="
echo "TERM_PROGRAM: $TERM_PROGRAM"
echo "TERM_PROGRAM_VERSION: $TERM_PROGRAM_VERSION"
echo "VSCODE_PID: $VSCODE_PID"
echo "VSCODE_IPC_HOOK_CLI: $VSCODE_IPC_HOOK_CLI"
echo "VSCODE_RESOLVING_ENVIRONMENT: $VSCODE_RESOLVING_ENVIRONMENT"
```

---

## 2

*[truncated — see source for full prompt]*