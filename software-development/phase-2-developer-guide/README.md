# PHASE 2 DEVELOPER GUIDE

> **Created:** 2026-02-02
**Issue:** #322 - Server Layer Refactor

This guide documents the thin adapter pattern for implementing v2 API routes.

---

#

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Phase 2: Developer Guide - V2 Router Implementation

**Created:** 2026-02-02
**Issue:** #322 - Server Layer Refactor

This guide documents the thin adapter pattern for implementing v2 API routes.

---

## Core Principle: Thin Adapters

V2 routers are **thin HTTP adapters** that delegate all business logic to core modules.

```
┌─────────────────────────────────────────────────────────────────┐
│                           HTTP Layer                            │
│  ┌─────────────┐    ┌─────────────┐    ┌─────────────────────┐  │
│  │ Parse Input │ -> │ Call Core   │ -> │ Transform Response  │  │
│  │ (Pydantic)  │    │ (workspace) │    │ (HTTP status, JSON) │  │
│  └─────────────┘    └─────────────┘    └─────────────────────┘  │
└─────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                          Core Layer                             │
│  ┌─────────────────────────────────────────────────────────┐    │
│  │ core.blockers, core.prd, core.tasks, core.runtime, ...  │    │
│  │ (Headless - No FastAPI imports - Works with CLI too)    │    │
│  └─────────────────────────────────────────────────────────┘    │
└─────────────────────────────────────────────────────────────────┘
```

---

## Implementation Template

### 1. File Structure

Create router at `codeframe/ui/routers/{resource}_v2.py`:

```python
"""V2 {Resource} router - delegates to core/{resource} module.

Routes:
    GET  /api/v2/{resource}             - List resources
    GET  /api/v2/{resource}/{id}        - Get specific resource
    POST /api/v2/{resource}             - Create resource
    PATCH /api/v2/{resource}/{id}       - Update resource
    DELETE /api/v2/{resource}/{id}      - Delete resource
"""

import logging
from typing import Optional

from fastapi import APIRouter, Depends, HTTPException, Query
from pydantic import BaseModel, Field

from co

*[truncated — see source for full prompt]*