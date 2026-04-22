# SYSTEM OVERVIEW

> This document explains exactly what OOS is, what each component does, and how everything fits together.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# OOS System Overview - What Everything Actually Does

This document explains exactly what OOS is, what each component does, and how everything fits together.

## 🎯 The Big Picture

**OOS = Project Bootstrap + Management Tools**

Think of it like this:
- **Core Function**: "I want to start a new project with AI tools properly configured"
- **Extended Function**: "I want to monitor, test, and maintain my development environment"

## 📦 What You Actually Have

### **Level 1: Core OOS (Your Original System)**
```
scripts/bootstrap.sh                    # "Set up a new project"
.agents/runners/run_claude.sh   # "Run Claude with proper environment"
bin/safe_source_env.sh         # "Load secrets from 1Password safely"
```

**This is the essential OOS.** Everything else is optional.

### **Level 2: Enhanced Management (What We Added)**
```
scripts/bootstrap_enhanced.sh           # "Bootstrap with pre-flight checks"
bin/diagnose.sh                # "Fix problems automatically"
bin/health_monitor.sh          # "Watch everything continuously"
bin/run_tests.sh              # "Ensure everything works"
bin/security_audit.sh         # "Check for security issues"
bin/performance_monitor.sh    # "Profile and optimize"
bin/template_manager.sh       # "Create projects from templates"
bin/key_rotator.sh            # "Manage API keys automatically"
```

**These are power tools for serious development.**

### **Level 3: External Integrations (Optional)**
```
Archon MCP Server              # External task management service
Dashboard (dashboard/)         # Web interface for monitoring
```

**You can ignore these entirely if you want.**

## 🤔 Common Confusions Explained

### **"Is Archon part of OOS?"**
**NO.** Archon is a separate service that OOS can optionally talk to.

- **Archon**: External task management server (like Jira, but simpler)
- **OOS**: Project bootstrap and management tools
- **They can work together, but OOS works fine without Archon**

### **"What does atlas.db have 

*[truncated — see source for full prompt]*