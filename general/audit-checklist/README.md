# AUDIT CHECKLIST

> **Purpose**: Verify each module complies with 5 governance rules from AGENTS.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Sighthound Content Relay — Governance Audit Checklist

**Purpose**: Verify each module complies with 5 governance rules from AGENTS.md
**Duration**: ~30 minutes total (5 min per module)
**Output**: Fill `AUDIT_RESPONSES.json` for each issue found, then run parser

---

## Rules Being Audited

1. **Forms & Input Behavior (MUST)**
   - All inputs expose clear validation states (error, success, disabled, loading)
   - Required fields enforced at UI + API
   - Inline errors shown near fields (not just toast)
   - No silent submit failure

2. **Feedback & System Status (MUST)**
   - Every action produces visible feedback (success/error/loading)
   - Long-running actions show progress
   - No uncertain or silent actions

3. **Error Handling (MUST)**
   - All errors human-readable and actionable
   - Errors categorized (validation/system/permission)
   - No raw errors or stack traces
   - Failed actions don't leave UI in inconsistent state

4. **Permissions Enforcement (MUST)**
   - Supabase RLS is source of truth (frontend checks UX-only)
   - Every feature defines who can view/edit/perform actions
   - No feature ships without RLS coverage

5. **Table Invariants (MUST)**
   - Fixed row heights (no expansion)
   - Single-line truncation with tooltip
   - Pagination controls stable (no shifting)
   - Overflow constraints enforced

---

## Module 1: Dashboard (`/dashboard`)

### Setup
1. Log in as **writer** user (non-admin)
2. Navigate to Dashboard
3. Have a blog in each queue ready (or create one)

### 1.1 Forms & Input Behavior

**Test: Status Update Inline**
- [ ] Click inline status dropdown on any blog row
- [ ] Try to submit without selecting a value → does it block or submit silently?
- [ ] Does error appear inline or only as toast?
- **Issue?** Record in `AUDIT_RESPONSES.json`

**Test: Bulk Action**
- [ ] Select 2-3 rows
- [ ] Click bulk action button
- [ ] Does it show a confirmation dialog with clear action description?
- [ ] Can you cancel?
- [ ] If action req

*[truncated — see source for full prompt]*