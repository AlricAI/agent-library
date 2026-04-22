# Sprint4 Testing Checklist

> ## Pre-Demo Setup Verification

### 1. Environment Check
- [ ] Verify staging server is running: `pm2 list`
  - [ ] Backend status: **online** (port 1

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Sprint 4 Multi-Agent Coordination - Manual Test Checklist

## Pre-Demo Setup Verification

### 1. Environment Check
- [ ] Verify staging server is running: `pm2 list`
  - [ ] Backend status: **online** (port 14200)
  - [ ] Frontend status: **online** (port 14100)
- [ ] Check backend health: `curl http://localhost:14200/`
  - Expected: `{"status":"online","service":"CodeFRAME Status Server"}`
- [ ] Check frontend loads: Open http://localhost:14100 in browser
  - Expected: Frontend UI loads with "Loading projects..." or project list

### 2. Database Initialization
- [ ] Verify database exists: `ls -la staging/.codeframe/state.db`
- [ ] Check database schema has latest columns:
  ```bash
  sqlite3 staging/.codeframe/state.db "PRAGMA table_info(tasks);" | grep parent_issue_number
  ```
  - Expected: Column exists with parent_issue_number field

---

## Phase 1: Agent Pool Manager (Task 4.3.1)

### Test 1.1: Agent Creation
- [ ] **Test**: Create multiple agent types
  ```python
  # In Python REPL or test script
  from codeframe.agents.agent_pool_manager import AgentPoolManager
  from codeframe.persistence.database import Database

  db = Database("staging/.codeframe/state.db")
  pool = AgentPoolManager(project_id=1, db=db, max_agents=10)

  # Create different agent types
  backend_id = pool.create_agent("backend")
  frontend_id = pool.create_agent("frontend")
  test_id = pool.create_agent("test")

  print(f"Created agents: {backend_id}, {frontend_id}, {test_id}")
  ```
- [ ] **Expected**: Agent IDs like `backend-worker-001`, `frontend-worker-002`, `test-worker-003`
- [ ] **Verify**: `pool.get_agent_status()` shows all 3 agents with status "idle"

### Test 1.2: Agent Pool Capacity Limit
- [ ] **Test**: Create agents until max capacity reached
  ```python
  # Try to create 11 agents (max is 10)
  try:
      for i in range(11):
          pool.create_agent("backend")
  except RuntimeError as e:
      print(f"✓ Capacity limit enforced: {e}")
  ```
- [ ] **Expected**: Runtim

*[truncated — see source for full prompt]*