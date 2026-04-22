# SOCIAL POST ASSIGNMENT VISUAL GUIDE

> ## What is Social Post Assignment?

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Social Post Assignment Event Support - Visual & Implementation Guide

## What is Social Post Assignment?

### Current Social Post Workflow Roles

Social posts have **two role-based actors**:

```
┌─────────────────────────────────────────────────────┐
│          Social Post Workflow Roles                 │
├─────────────────────────────────────────────────────┤
│                                                     │
│  EDITOR (editor_user_id)                           │
│  ├─ Status: draft                                  │
│  ├─ Status: changes_requested                      │
│  ├─ Status: ready_to_publish                       │
│  └─ Status: awaiting_live_link                     │
│                                                     │
│  ADMIN (admin_owner_id)                            │
│  ├─ Status: in_review                              │
│  └─ Status: creative_approved                      │
│                                                     │
│  Both → Status: published                          │
│                                                     │
└─────────────────────────────────────────────────────┘
```

### Database Fields Ready (Already Exist)

```sql
-- These fields are ALREADY in the social_posts table:
ALTER TABLE social_posts ADD COLUMN editor_user_id UUID;     -- Who edits the post
ALTER TABLE social_posts ADD COLUMN admin_owner_id UUID;     -- Who reviews/approves
```

### Audit System Ready (Already Implemented)

```sql
-- When either field changes, this trigger fires automatically:
IF new.editor_user_id IS DISTINCT FROM old.editor_user_id
   OR new.admin_owner_id IS DISTINCT FROM old.admin_owner_id THEN
   -- Logs 'social_post_assignment_changed' event
   -- Triggers notification
END IF;
```

---

## Why We're Not Implementing UI Now

### 1. **No Product Decision Yet**

**Question**: Should social post editors and admins be reassigned?

Currently:
- `editor_user_id` is set to `created_by` (the creator)
- `admin_owner_id` is set when

*[truncated — see source for full prompt]*