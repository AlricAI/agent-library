# QUICK REFERENCE AGENT ASSIGNMENT

> ## TL;DR

**Before**: One agent per project (broken architecture)
```python
agent = WorkerAgent(agent_id="backend-001", project_id=1)  # ❌ Locked to p

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Quick Reference: Agent-Project Assignment API

## TL;DR

**Before**: One agent per project (broken architecture)
```python
agent = WorkerAgent(agent_id="backend-001", project_id=1)  # ❌ Locked to project 1
```

**After**: Agents can work on multiple projects
```python
agent = WorkerAgent(agent_id="backend-001")  # ✅ Reusable resource
agent.assign_to_project(project_id=1, role="primary_backend")
agent.assign_to_project(project_id=2, role="consultant")
```

---

## Python API Quick Reference

### 1. Agent Lifecycle

```python
from codeframe.persistence.database import Database

db = Database("state.db")
db.initialize()

# Create an agent (reusable resource)
from codeframe.core.models import AgentMaturity

agent_id = db.create_agent(
    agent_id="backend-001",
    agent_type="backend",
    provider="claude",
    maturity_level=AgentMaturity.D4  # Use enum member, not string
)

# Assign to projects
db.assign_agent_to_project(
    project_id=1,
    agent_id="backend-001",
    role="primary_backend"
)

db.assign_agent_to_project(
    project_id=2,
    agent_id="backend-001",
    role="code_reviewer"
)
```

### 2. Querying Assignments

```python
# Find all agents on a project
agents = db.get_agents_for_project(project_id=1, active_only=True)
for agent in agents:
    print(f"{agent['agent_id']}: {agent['role']}")

# Find all projects for an agent
projects = db.get_projects_for_agent(agent_id="backend-001", active_only=True)
for project in projects:
    print(f"Project {project['project_id']}: {project['role']}")

# Check specific assignment
assignment = db.get_agent_assignment(project_id=1, agent_id="backend-001")
if assignment and assignment['is_active']:
    print(f"Active assignment: {assignment['role']}")
```

### 3. Task Assignment (with validation)

```python
# ❌ OLD WAY (no validation)
db.conn.execute(
    "UPDATE tasks SET assigned_to = ? WHERE id = ?",
    ("backend-001", 42)
)

# ✅ NEW WAY (validates agent is on project)
def assign_task_to_agent(db, task_id, ag

*[truncated — see source for full prompt]*