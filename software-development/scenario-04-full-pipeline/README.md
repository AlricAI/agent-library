# Scenario 04 Full Pipeline

> **Pattern:** `full-team-pipeline`  
**Teams used:** `code_review_team` → `documentation_team` → `qa_team` (sequential)  
**Sub-agents:** Spec-reviewer

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Scenario 04: Full Team Agent Pipeline

**Pattern:** `full-team-pipeline`  
**Teams used:** `code_review_team` → `documentation_team` → `qa_team` (sequential)  
**Sub-agents:** Spec-reviewer, quality-reviewer, doc-writer, doc-reviewer, changelog-updater, test-generator, test-verifier

---

## Goal

Validate that all three agent teams can be chained sequentially in a complete pipeline, where each team's completion triggers the next. This represents the most complete quality assurance flow in the framework.

---

## Pipeline Flow

```
Code Change
    │
    ▼
code_review_team
    ├── spec-reviewer ✅
    └── quality-reviewer ✅
    │
    ▼
documentation_team
    ├── doc-writer ✅
    ├── doc-reviewer ✅
    └── changelog-updater ✅
    │
    ▼
qa_team
    ├── test-generator ✅
    └── test-verifier ✅
    │
    ▼
Task Complete ✅
```

---

## What This Tests

| Test Point | Description |
|---|---|
| Sequential team dispatch | All 3 teams dispatched in correct order |
| Context threading | Each team receives the same base payload |
| All teams dispatch cleanly | Each returns exit code 0 with a valid manifest |
| Run ID uniqueness | Each team dispatch has a unique run ID |

---

## Run

```bash
python3 execution/run_test_scenario.py --scenario 4
```

---

## Expected Output

```json
{
  "scenario": "scenario_04_full_pipeline",
  "pattern": "full-team-pipeline",
  "status": "pass",
  "steps": [
    { "step": "dispatch code_review_team", "exit_code": 0, "run_id": "abc12345" },
    { "step": "dispatch documentation_team", "exit_code": 0, "run_id": "def67890" },
    { "step": "dispatch qa_team", "exit_code": 0, "run_id": "ghi11223" },
    {
      "step": "validate full pipeline completed",
      "teams_dispatched": ["code_review_team", "documentation_team", "qa_team"],
      "all_passed": true
    }
  ]
}
```

---

## Manual Walkthrough

```bash
# After implementing a feature:

# Step 1: Code review
python3 execution/dispatch_agent_team.py \
  --team code_review_team \
  --payload 

*[truncated — see source for full prompt]*