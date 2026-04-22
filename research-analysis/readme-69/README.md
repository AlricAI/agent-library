# README

> ## Overview

The KG Query Agent provides conversational access to the arXiv research knowledge graph stored in Neo4j. It uses Claude Agent SDK with cu

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# KG Query Agent - Agentic Neo4j Queries

## Overview

The KG Query Agent provides conversational access to the arXiv research knowledge graph stored in Neo4j. It uses Claude Agent SDK with custom MCP tools to enable **true agentic behavior** - Claude iteratively queries the database until it finds the answer.

## Architecture

### Agentic Loop

```
User Query → Claude Agent SDK → Claude AI
                ↓
          ToolUseBlock
                ↓
    Neo4j SDK MCP Server
                ↓
         neo4j_tools.py
                ↓
         Neo4j Database
                ↓
         Results → Claude
                ↓
    (Repeat until satisfied)
                ↓
            Final Answer
```

### Components

1. **agent.py** - Main agent orchestrator using `ClaudeSDKClient`
2. **neo4j_sdk_tools.py** - MCP tool definitions with `@tool` decorator
3. **neo4j_tools.py** - Low-level Neo4j driver wrapper
4. **index.ts** - TypeScript wrapper for SMS bot integration

### Tools Available to Claude

- `mcp__neo4j__execute_cypher` - Execute Cypher queries
- `mcp__neo4j__get_schema` - Get database schema
- `mcp__neo4j__get_data_quality_status` - Check clean data boundaries

## Key Features

### True Agentic Behavior

Claude decides:
- What queries to run
- When to explore vs drill down
- How to adapt when data is missing
- When it has enough information to answer

Example query flow (15 tool calls):
1. Get schema (understand structure)
2. Get data quality status (check boundaries)
3. Exploratory query (see what's available)
4. Refined query 1 (filter by criteria)
5. Refined query 2 (different approach)
...
15. Final query (get specific results)

### No Hardcoded Templates

Unlike the previous version, there are NO pre-defined query templates or intent classifiers. Claude writes all queries dynamically based on:
- User's question
- Database schema
- Previous query results
- Data quality constraints

## Usage

### SMS Command

```
kg <your question>
```

Examples:
- `kg give me 2 u

*[truncated — see source for full prompt]*