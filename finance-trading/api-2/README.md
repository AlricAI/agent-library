# API

> ## Overview

The DeFi Agents API is a RESTful JSON API providing access to 78 production-ready AI agent definitions for DeFi, portfolio management, tr

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# DeFi Agents API Documentation

## Overview

The DeFi Agents API is a RESTful JSON API providing access to 78 production-ready AI agent definitions for DeFi, portfolio management, trading, and Web3 workflows. All agents are available in 30+ languages.

**Base URL**: `https://sperax.click`

---

## Endpoints

### 1. **Get All Agents (English)**

Retrieve the complete index of all 78 agents in English.

```
GET /index.json
```

**Response**: Array of agent objects with full definitions

**Example**:

```bash
curl https://sperax.click/index.json | jq '.[] | {id: .identifier, name: .meta.title}'
```

---

### 2. **Get Agents in Specific Language**

Retrieve all agents in a supported language.

```
GET /index.{locale}.json
```

**Supported Locales**:

- `en-US` (English)
- `ar` (Arabic)
- `bg-BG` (Bulgarian)
- `zh-CN` (Chinese Simplified)
- `zh-TW` (Chinese Traditional)
- `de-DE` (German)
- `es-ES` (Spanish)
- `fa-IR` (Persian)
- `fr-FR` (French)
- `it-IT` (Italian)
- `ja-JP` (Japanese)
- `ko-KR` (Korean)
- `nl-NL` (Dutch)
- `pl-PL` (Polish)
- `pt-BR` (Portuguese Brazilian)
- `ru-RU` (Russian)
- `tr-TR` (Turkish)
- `vi-VN` (Vietnamese)

**Example**:

```bash
curl https://sperax.click/index.zh-CN.json # Get all agents in Chinese
```

---

### 3. **Get Single Agent**

Retrieve a specific agent definition by ID.

```
GET /{agent-id}.json
```

**Example**:

```bash
curl https://sperax.click/sperax-dashboard.json
```

---

### 4. **Get Single Agent in Specific Language**

```
GET /{agent-id}.{locale}.json
```

**Example**:

```bash
curl https://sperax.click/sperax-dashboard.fr-FR.json # French
```

---

### 5. **Agent Manifest (Machine-Readable Index)**

Get structured metadata about all agents for indexing.

```
GET /agents-manifest.json
```

**Example**:

```bash
curl https://sperax.click/agents-manifest.json
```

---

## Agent Schema

Each agent follows this JSON structure:

```json
{
  "author": "string", // Agent creator/organization
  "config": {
    "systemRole": "str

*[truncated — see source for full prompt]*