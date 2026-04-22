# ARCHON INTEGRATION

> This guide explains how to properly integrate OOS with Archon MCP for project management while ensuring complete project separation and isolation.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Archon Integration Guide - Project Separation & Best Practices

This guide explains how to properly integrate OOS with Archon MCP for project management while ensuring complete project separation and isolation.

## 🎯 Overview

Archon MCP provides project and task management capabilities integrated with OOS. The key principle is **complete project isolation** - each project operates independently with its own:

- Unique project ID
- Isolated task management
- Separate documentation
- Independent monitoring
- Isolated security audit trails

## 🏗️ Project Architecture

### Project Isolation Model

```
Archon Server
├── Project Alpha (ID: 550e8400-...)
│   ├── Tasks (filtered by project_id)
│   ├── Documents (scoped to project)
│   ├── Features (project-specific)
│   └── Versions (project history)
├── Project Beta (ID: 7a8b9c0d-...)
│   ├── Tasks (completely separate)
│   ├── Documents (independent)
│   ├── Features (isolated)
│   └── Versions (separate history)
└── Project Gamma (ID: 2f3e4d5c-...)
    └── (fully isolated scope)
```

### Environment Configuration

Each project maintains its own `.env` file with unique identifiers:

```bash
# Project Alpha - Authentication Service
ARCHON_PROJECT_ID=550e8400-e29b-41d4-a716-446655440000
ARCHON_URL=http://localhost:8051/mcp
PROJECT_NAME=auth-service
PROJECT_TYPE=api

# Project Beta - E-commerce Frontend
ARCHON_PROJECT_ID=7a8b9c0d-1e2f-3a4b-5c6d-7e8f90123456
ARCHON_URL=http://localhost:8051/mcp
PROJECT_NAME=ecommerce-web
PROJECT_TYPE=web-app
```

## 🚀 Step-by-Step Integration

### 1. Initial Project Setup

#### Create New Project in Archon
```javascript
// In Claude Code with Archon MCP
mcp__archon__create_project({
    title: "Authentication Service",
    description: "JWT-based authentication API with OAuth2 integration for multi-tenant SaaS platform",
    github_repo: "https://github.com/myorg/auth-service"
})

// Response includes:
// {
//   "success": true,
//   "project_id": "550e8400-e29b-41d4-a716-446655440000",

*[truncated — see source for full prompt]*