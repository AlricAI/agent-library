# WORKFLOW

> > Comprehensive guide to the entire agent lifecycle: from creation → translation → build → deployment

---

## 📋 Table of Contents

- [Overview](#ove

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🔄 Complete Development Workflow

> Comprehensive guide to the entire agent lifecycle: from creation → translation → build → deployment

---

## 📋 Table of Contents

- [Overview](#overview)
- [Quick Reference](#quick-reference)
- [Architecture](#architecture)
- [Full Workflow](#full-workflow)
- [Local Development](#local-development)
- [CI/CD Pipeline](#cicd-pipeline)
- [Domain Management](#domain-management)
- [For Contributors](#for-contributors)
- [For Fork Maintainers](#for-fork-maintainers)

---

## Overview

This repository uses an automated workflow that takes agent definitions and:

1. ✅ Translates them to 30+ languages
2. ✅ Builds a CDN-ready index
3. ✅ Deploys to GitHub Pages
4. ✅ Preserves custom domains automatically

**Key Principle:** Submit in English, everything else is automatic.

---

## Quick Reference

### For Contributors

```bash
# 1. Create agent
echo '{ ... }' > src/my-agent.json

# 2. Submit PR
git add src/my-agent.json
git commit -m "feat: Add My Agent"
git push

# Done! CI handles translation + deployment
```

### For Maintainers

```bash
# Setup
git clone https://github.com/yourusername/defi-agents
cd defi-agents
bun install
echo "OPENAI_API_KEY=sk-xxx" > .env

# Development cycle
bun run format # Translate agents
bun run build  # Build public index
bun run test   # Validate everything

# Deploy (automatic on push to main)
git push origin main
```

---

## Architecture

### Directory Structure

```
defi-agents/
├── CNAME                          # Your custom domain (optional)
├── .env                           # Local environment variables (gitignored)
│   └── OPENAI_API_KEY=sk-xxx
│
├── src/                           # 📝 Agent source files (English only)
│   ├── agent-1.json
│   ├── agent-2.json
│   └── sperax-dashboard.json
│
├── locales/                       # 🌍 30+-language translations (auto-generated)
│   ├── agent-1/
│   │   ├── index.json             # en-US (default)
│   │   ├── index.zh-CN.json       # Chinese
│   │   ├──

*[truncated — see source for full prompt]*