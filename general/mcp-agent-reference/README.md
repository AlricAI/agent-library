# MCP AGENT REFERENCE

> **Complete guide to building and deploying MCP agents for the platform**

---

## 🎯 Quick Start: Your First MCP Agent

### 1. Create Agent Structure


## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 📚 VorstersNV – MCP Agent Reference Library

**Complete guide to building and deploying MCP agents for the platform**

---

## 🎯 Quick Start: Your First MCP Agent

### 1. Create Agent Structure

```bash
mkdir -p agents/crm_agent
cd agents/crm_agent

# Create files
touch __init__.py
touch server.py        # MCP server implementation
touch tools.py         # Tool definitions
touch config.yml       # Agent configuration
touch README.md
```

### 2. Implement MCP Server

```python
# agents/crm_agent/server.py
from mcp.server.fastmcp import FastMCP
from pydantic import BaseModel
from typing import List
import asyncio

mcp = FastMCP("CRM Agent")

class CustomerModel(BaseModel):
    id: str
    name: str
    email: str
    phone: str
    status: str  # active | inactive | vip
    created_at: str

class CustomerSearchInput(BaseModel):
    query: str
    limit: int = 10

# ============= TOOLS =============

@mcp.tool()
async def search_customers(input: CustomerSearchInput) -> List[CustomerModel]:
    """
    Search for customers by name, email, or phone.
    
    Perfect for finding existing customers quickly.
    """
    # TODO: Implement database query
    # return await db.customers.search(input.query, limit=input.limit)
    return []

@mcp.tool()
async def get_customer(customer_id: str) -> CustomerModel:
    """Get detailed customer information by ID"""
    # return await db.customers.get(customer_id)
    pass

@mcp.tool()
async def create_customer(name: str, email: str, phone: str) -> CustomerModel:
    """Create a new customer record"""
    # return await db.customers.create(name=name, email=email, phone=phone)
    pass

@mcp.tool()
async def update_customer(customer_id: str, **updates) -> CustomerModel:
    """Update customer information"""
    # return await db.customers.update(customer_id, updates)
    pass

@mcp.tool()
async def get_customer_orders(customer_id: str) -> List[dict]:
    """Get all orders from a specific customer"""
    # return await db.orders.filt

*[truncated — see source for full prompt]*