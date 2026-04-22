# BUG REPORT WORKFLOW

> **ModPorter AI Beta Program**

---

## Bug Report Process

### User Submission Flow

```
1. User encounters bug
   ↓
2. Submits bug report (UI or Disc

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Bug Report Workflow

**ModPorter AI Beta Program**

---

## Bug Report Process

### User Submission Flow

```
1. User encounters bug
   ↓
2. Submits bug report (UI or Discord)
   ↓
3. Auto-acknowledgment sent
   ↓
4. Triage by support team
   ↓
5. Assigned to developer
   ↓
6. Fix developed and tested
   ↓
7. Deployed to production
   ↓
8. User notified of fix
```

---

## Bug Report Template

### Required Information

**Basic Info:**
- Title (clear, concise description)
- Description (what happened)
- Severity (low, medium, high, critical)
- Conversion ID (if applicable)

**Technical Details:**
- Steps to reproduce
- Expected behavior
- Actual behavior
- Browser/OS (if web issue)
- Mod file (if conversion issue)

**Optional:**
- Screenshots/videos
- Log files
- Workarounds found

---

## Severity Levels

### Critical 🔴
**Definition:** Complete service outage or data loss

**Examples:**
- Service completely down
- All conversions failing
- User data lost/corrupted
- Security vulnerability

**Response Time:** < 4 hours
**Fix Target:** < 24 hours

### High 🟠
**Definition:** Major feature broken

**Examples:**
- Conversion fails for specific mod types
- Download not working
- Login issues
- Payment processing errors

**Response Time:** < 24 hours
**Fix Target:** < 72 hours

### Medium 🟡
**Definition:** Minor feature broken, workaround exists

**Examples:**
- UI elements misaligned
- Slow performance
- Non-critical feature not working
- Minor visual bugs

**Response Time:** < 48 hours
**Fix Target:** < 1 week

### Low 🟢
**Definition:** Cosmetic issue or minor inconvenience

**Examples:**
- Typos in UI
- Color inconsistencies
- Minor UX improvements
- Feature requests

**Response Time:** < 1 week
**Fix Target:** Next release

---

## Bug Report Channels

### Discord (#bug-reports)

**Format:**
```
**Title:** [Brief description]
**Severity:** [low/medium/high/critical]
**Conversion ID:** [if applicable]
**Description:** [What happened]
**Steps to Reproduce:**
1. [St

*[truncated — see source for full prompt]*