# TECHNICAL IMPLEMENTATION

> **Detailed technical specifications for cloud platform development**

---

## 📋 Table of Contents

1. [MCP Agent Development](#mcp-agent-development)

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🛠️ VorstersNV Cloud – Technical Implementation Guide

**Detailed technical specifications for cloud platform development**

---

## 📋 Table of Contents

1. [MCP Agent Development](#mcp-agent-development)
2. [Microservices Setup](#microservices-setup)
3. [Cloud Infrastructure](#cloud-infrastructure)
4. [API Specifications](#api-specifications)
5. [Database Design](#database-design)
6. [Security Implementation](#security-implementation)
7. [DevOps & CI/CD](#devops--cicd)

---

## 🤖 MCP Agent Development

### MCP Server Structure

```python
# agents/mcp_server.py
from mcp.server.fastmcp import FastMCP
from pydantic import BaseModel
import asyncio

# Initialize MCP server
mcp = FastMCP("CRM Agent")

class SearchCustomersInput(BaseModel):
    query: str
    limit: int = 10

class Customer(BaseModel):
    id: str
    name: str
    email: str
    created_at: str

@mcp.tool()
async def search_customers(input: SearchCustomersInput) -> List[Customer]:
    """
    Search customers by name, email, or ID.
    
    Args:
        query: Search term (name, email, phone)
        limit: Maximum results
    
    Returns:
        List of matching customers
    """
    # Implementation connects to tenant-scoped DB
    results = await db.query_customers(
        tenant_id=current_tenant_id,
        query=input.query,
        limit=input.limit
    )
    return [Customer(**r) for r in results]

@mcp.tool()
async def get_customer_orders(customer_id: str) -> List[dict]:
    """Get all orders for a customer"""
    return await db.get_orders(current_tenant_id, customer_id)

@mcp.tool()
async def create_customer(name: str, email: str) -> Customer:
    """Create a new customer"""
    result = await db.create_customer(
        tenant_id=current_tenant_id,
        name=name,
        email=email
    )
    return Customer(**result)

if __name__ == "__main__":
    mcp.run()
```

### Agent Service Entry Point

```python
# services/agents/crm_agent.py
from anthropic import AsyncAnthropic
from mcp.

*[truncated — see source for full prompt]*