# AGENT COMMUNICATION

> ## Inleiding

Dit document beschrijft hoe agents met elkaar communiceren, hoe webhooks werken, en hoe het orchestration systeem orders en events route

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🔌 AGENT COMMUNICATIE & ORCHESTRATION

## Inleiding

Dit document beschrijft hoe agents met elkaar communiceren, hoe webhooks werken, en hoe het orchestration systeem orders en events routert naar de juiste agents.

---

## 1️⃣ Agent Communication Patterns

### Pattern 1: Sequential (Serie)

**Gebruik:** Normale order processing
- Stap 1 wacht tot Stap 2 klaar is
- Sync & predictable

```python
async def sequential_workflow(order):
    """
    A → B → C (wachten op elkaar)
    """
    
    # Step 1: Validation (wacht)
    validation = await runner.run_agent(
        "order_verwerking_agent",
        user_input=order_data
    )
    
    if not validation['success']:
        return {"error": "Order invalid"}
    
    # Step 2: Fraud check (wacht op validation)
    fraud = await runner.run_agent(
        "fraude_detectie_agent",
        user_input={
            **order_data,
            "validation_result": validation
        }
    )
    
    # Step 3: Email (wacht op fraud)
    if fraud['fraud_score'] < 0.8:
        email = await runner.run_agent(
            "email_template_agent",
            user_input={
                **order_data,
                "fraud_score": fraud['fraud_score']
            }
        )
    
    return {
        "success": True,
        "validation": validation,
        "fraud": fraud,
        "email": email
    }

# Usage
order = {
    "order_id": "ORD123",
    "customer_id": "CUST456",
    "items": [...],
    "total": 99.99
}

result = await sequential_workflow(order)
```

**Voordelen:**
- ✅ Deterministic
- ✅ Easy debugging
- ✅ Clear order of operations

**Nadelen:**
- ❌ Kan langzaam zijn (2-3 seconden)
- ❌ Gevoelig voor failures

---

### Pattern 2: Parallel (Gelijktijdig)

**Gebruik:** Onafhankelijke checks
- Stap 1 & 2 tegelijk
- Sneller (optimaal ~1.5 sec)

```python
async def parallel_workflow(order):
    """
    A → [B | C] (tegelijk, dan D)
    """
    
    # Step 1: Validation (altijd eerst)
    validation = await runner.run_agent(

*[truncated — see source for full prompt]*