# CONTRIBUTING

> Thank you for contributing to the AI Agents Library Agent Marketplace!

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Contributing to AI Agents Library Agents

Thank you for contributing to the AI Agents Library Agent Marketplace! This guide will help you submit high-quality agents.

## Quick Start

1. Fork the repository
2. Create your agent in `/src/`
3. Test thoroughly
4. Submit a Pull Request

## Submission Guidelines

### Agent Requirements

✅ **Must Have:**

- Unique identifier (no duplicates)
- Clear, descriptive title
- Concise description (160-200 characters)
- Relevant emoji avatar
- 3-8 appropriate tags
- Well-structured system prompt
- Valid JSON format

❌ **Not Allowed:**

- Copyrighted content
- Malicious or harmful prompts
- Personal/private information
- Spam or low-effort submissions
- Duplicate agents (check existing first)

### File Structure

```
src/
  your-agent-name.json          # Main agent file (English)
  your-agent-name.zh-CN.json    # Optional: Chinese translation
```

If you only provide English, our automated i18n workflow will translate to 30+ languages.

### Agent Template

Create `/src/your-agent-name.json`:

```json
{
  "author": "your-github-username",
  "config": {
    "systemRole": "You are [detailed system prompt]..."
  },
  "identifier": "your-agent-name",
  "meta": {
    "title": "Your Agent Title",
    "description": "Brief description of what your agent does",
    "avatar": "🤖",
    "tags": ["defi", "trading", "relevant", "keywords"]
  },
  "schemaVersion": 1
}
```

### Naming Conventions

**Identifier** (filename):

- Use lowercase
- Use hyphens for spaces: `sperax-yield-optimizer`
- No special characters except hyphens
- Keep it descriptive but concise

**Title** (display name):

- Use Title Case
- Can include spaces
- Clear and professional

## Categories & Tags

### Primary Categories

- `defi` - DeFi protocols, yield, liquidity
- `trading` - Market analysis, strategies
- `security` - Audits, vulnerability analysis
- `development` - Coding, smart contracts
- `analytics` - Data analysis, metrics
- `education` - Learning, tutorials
- 

*[truncated — see source for full prompt]*