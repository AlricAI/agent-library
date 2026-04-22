# IMPLEMENTATION CHECKLIST

> ## 📋 Fase 3: Agent Integration (Weken 1-4)

### 🔴 WEEK 1-2: Order Processing Workflow

#### Pre-setup
- [ ] Ollama draait lokaal (port 11434)
- [ ] 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ✅ IMPLEMENTATION CHECKLIST – Agent-Gebaseerde VorstersNV Opbouw

## 📋 Fase 3: Agent Integration (Weken 1-4)

### 🔴 WEEK 1-2: Order Processing Workflow

#### Pre-setup
- [ ] Ollama draait lokaal (port 11434)
- [ ] Docker Compose services draaien (PostgreSQL, Redis)
- [ ] FastAPI project setup (`api/main.py` exists)
- [ ] Agent YAML files in `/agents/` directory

#### Agent Runner Setup
- [ ] Implement `ollama/agent_runner.py`
  - [ ] `_load_all_agents()` method
  - [ ] `run_agent()` async method
  - [ ] Prompt loading & substitution
  - [ ] Logging to database

- [ ] Create database models:
  - [ ] `Order` model
  - [ ] `AgentExecutionLog` model
  - [ ] `OrderProcessingError` model

#### Order API Router
- [ ] Create `api/routers/orders.py`
- [ ] `POST /api/orders/` endpoint
  - [ ] Request validation (Pydantic)
  - [ ] Call to `order_verwerking_agent`
  - [ ] Call to `fraude_detectie_agent` (parallel)
  - [ ] Call to `email_template_agent`
  - [ ] Call to `voorraad_advies_agent` (parallel)
  - [ ] Database save

- [ ] `GET /api/orders/{order_id}` endpoint
  - [ ] Retrieve order status
  - [ ] Show fraud score
  - [ ] Show email sent status

#### Webhook Handler
- [ ] Create `webhooks/handlers/order_handler.py`
- [ ] `POST /webhooks/order-created` endpoint
  - [ ] HMAC signature verification
  - [ ] Call to `handle_order_workflow()`
  - [ ] Error handling & logging

#### Testing
- [ ] Unit test for agent runner
- [ ] Integration test for order workflow
- [ ] Test with sample order JSON
- [ ] Verify all 5 agents called

**✅ Success Criteria:**
- Order created via API
- All agents executed successfully
- Order saved to database
- Email sent to customer
- Response time < 3 seconds

---

### 🟠 WEEK 2-3: Customer Support Workflow

#### Support Router
- [ ] Create `api/routers/support.py`

- [ ] `POST /api/support/chat` endpoint
  - [ ] Call to `klantenservice_agent`
  - [ ] Parse agent response for action
  - [ ] Conditional routing to sub-agents

#### Conditional Su

*[truncated — see source for full prompt]*