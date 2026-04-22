# NOTIFICATION USER NAMES

> Commit: `f6ca254` - Updated notification system to display actual user names instead of role labels.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# User Names in Notifications

Commit: `f6ca254` - Updated notification system to display actual user names instead of role labels.

## Overview
All notifications (Slack + in-app) now show the actual user responsible, not generic role labels like "Writer" or "Editor".

## Changes Made

### 1. **New Event Fields** (`UnifiedEvent`)
```typescript
// New fields added
targetUserName?: string;  // "Sarah Chen", "Alex Rodriguez", etc.
targetUserId?: string;    // UUID of the assigned user
```

### 2. **Message Builder Updates**
Notification messages now use actual user names with fallback:

```typescript
const targetUser = event.targetUserName || "team member";
```

## Before & After Examples

### Example 1: Blog Assignment

**BEFORE (In-App):**
```
Title: Blog Assignment
Message: "Q4 Strategy Blog" assigned to Writer
```

**AFTER (In-App):**
```
Title: Blog Assignment
Message: "Q4 Strategy Blog" assigned to Sarah Chen
```

**BEFORE (Slack):**
```
[Blog] Writer assigned
"Q4 Strategy Blog" (SH)
Next: Writing
```

**AFTER (Slack):**
```
[Blog] Writer assigned
"Q4 Strategy Blog" (SH)
Assigned to: Sarah Chen
Next: Writing
```

---

### Example 2: Awaiting Action

**BEFORE (In-App):**
```
Title: Action Needed
Message: "Campaign Post" needs publisher attention
```

**AFTER (In-App):**
```
Title: Action Needed
Message: "Campaign Post" awaiting action from Marcus Johnson
```

**BEFORE (Slack):**
```
[Social] Ready to publish
"Campaign Post" (SH)
Next: Publishing
```

**AFTER (Slack):**
```
[Social] Ready to publish
"Campaign Post" (SH)
Assigned to: Marcus Johnson
Next: Publishing
```

---

### Example 3: Social Post Reassignment

**BEFORE (In-App):**
```
Title: Social Post Reassigned
Message: "Black Friday Launch" reassigned to creative_approved
```

**AFTER (In-App):**
```
Title: Social Post Reassigned
Message: "Black Friday Launch" reassigned to Jordan Chen
```

**BEFORE (Slack):**
```
[Social] Creative approved
"Black Friday Launch" (RED)
```

**AFTER (Slack):**
```
[Social] Cr

*[truncated — see source for full prompt]*