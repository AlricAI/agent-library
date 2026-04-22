---
name: Testing Guide
description: > Last updated: v3.3.
model: claude-sonnet-4-5
---
# Cue — Manual Testing Guide

> Last updated: v3.3.0
> Covers all 9 action types across all 4 placements, categories, per-project appearance, and property key namespace

---

## Prerequisites

```shell
# Use Node 22 (required)
export PATH="/opt/homebrew/opt/node@22/bin:$PATH"
node --version  # must print v22.x.x

forge login
NODE_OPTIONS="--max-old-space-size=8192" forge deploy --environment production
forge install --upgrade --non-interactive --confirm-scopes --environment production \
  --site narendev.atlassian.net --product jira
```

## Pre-commit Checks

1. `npx tsc --noEmit` — must pass with zero errors
2. `forge lint` — must pass with zero errors (warnings for deprecated `app.name` and `storage` are pre-existing and acceptable)
3. No `any` types in TypeScript files
4. No direct `storage.get()` / `storage.set()` calls outside `src/storage/client.ts`
5. No `requestJira()` calls on component render — only on button click or in the resolver

---

## Test 1 — Global Admin UI

### T1.1: Categories — Create
1. Open **Jira Settings → Apps → Cue — Smart Actions & Buttons**
2. Click **+ Add Category**, type "Escalation", click **Create**
3. **Expected:** "Escalation" category box appears (collapsed or open), shows "0 buttons"
4. Click **+ Add Category**, type "Onboarding", click **Create**
5. **Expected:** Two category boxes visible

### T1.2: Categories — Rename
1. Click **Rename** on the "Escalation" box
2. Change name to "Escalation & Triage", click **Save**
3. **Expected:** Box header updates immediately

### T1.3: Category Accordion (expand/collapse)
1. Click **▼** on a category box header
2. **Expected:** Box collapses, icon changes to **▶**
3. Click **▶** to re-expand
4. **Expected:** Box opens showing its buttons (or empty message)

### T1.4: Create Button — OPEN_URL (in category)
1. Click **+ Create Button**
2. Fill: Label = "Open Runbook", Style = Primary, Category = "Escalation & Triage", Action Type = Open URL
3. URL: `https://wiki.example.com/{{project.key}}/runbook`
4. Select placements: Issue Panel
5. Click **Create Button**
6. **Expected:** Button appears inside the "Escalation & Triage" category box

### T1.5: Create All 9 Action Types
Create one button per type with these payloads:

| # | Label | Action Type | Key Payload | Category |
|---|-------|-------------|-------------|----------|
| 1 | Open Runbook | OPEN_URL | url: `https://wiki.example.com/{{issue.key}}` | Escalation & Triage |
| 2 | View Dashboard | OPEN_MODAL | url: `https://dashboard.example.com/{{project.key}}` | Onboarding |
| 3 | Move to Done | JIRA_TRANSITION | transitionId: `31` | — |
| 4 | Add Review Note | JIRA_COMMENT | commentTemplate: `Reviewed by {{user.displayName}} on {{date}}` | — |
| 5 | Assign to Lead | JIRA_ASSIGN | accountId: `<valid-account-id>` | — |
| 6 | Copy Reference | COPY_TEXT | copyTemplate: `{{issue.key}}: {{issue.summary}}` | — |
| 7 | Flag Escalated | SET_ISSUE_PROPERTY | suffix: `status`, value: `escalated`, type: `string` | Escalation & Triage |
| 8 | Run Sync | FORGE_FUNCTION | functionName: `custom-sync` | — |
| 9 | Create Story | CREATE_CHILD_ISSUE | parentIssueType: `Epic`, childIssueType: `Story`, mode: `form`, summary: `[{{issue.key}}] {{issue.summary}}` | Onboarding |

### T1.6: SET_ISSUE_PROPERTY — Namespace in form
1. Create a `SET_ISSUE_PROPERTY` button
2. **Expected:** The property key field label shows `"Property Key suffix (stored as cue.smartaction.{suffix})"`
3. Type `status` in the field, save
4. **Expected:** Button saved; on click the property key used is `cue.smartaction.status` (verify via REST after clicking)

### T1.7: Edit Button
1. Click **Edit** on any button, change label and payload, click **Update Button**
2. **Expected:** Changes reflected immediately in the category box

### T1.8: Delete Button
1. Click **Delete** on a button
2. **Expected:** Button removed from the category box

### T1.9: Categories — Delete
1. Click **Delete** on the "Onboarding" category
2. **Expected:** Category box removed; buttons that were in it move to the **Uncategorised** box at the bottom

### T1.10: Inline Validation
1. Leave label empty → **Expected:** "Label is required"
2. Enter label > 40 chars → **Expected:** "Label must be 40 characters or fewer"
3. Select OPEN_URL, leave URL empty → **Expected:** "URL is required"
4. Enter URL without http/https → **Expected:** "URL must start with http:// or https://"
5. Select CREATE_CHILD_ISSUE, leave childIssueType empty → **Expected:** "Child Issue Type is required"

### T1.11: Custom Success Message
1. Create a button, enter "Success Message" = "Report initiated"
2. Enable in project, click from issue
3. **Expected:** "Report initiated" appears in success banner

### T1.12: Show Last-Clicked Toggle
1. Create/edit a button, check "Show last-clicked time on button"
2. Enable in project, open an issue
3. **Expected:** "Last: Never" shown below the button
4. Click the button
5. **Expected:** Updates to "Last: just now"
6. Open a **different issue** with the same button
7. **Expected:** "Last: Never" — timestamps are per-issue

### T1.13: CREATE_CHILD_ISSUE — Direct Mode
1. Create a `CREATE_CHILD_ISSUE` button: parentIssueType = `Story`, childIssueType = `Sub-task`, mode = `direct`, summary = `Sub-task for {{issue.key}}`
2. Check "Use native sub-task hierarchy"
3. Enable in a project, set visibilityCondition = `Story`
4. Open a Story issue, click the button
5. **Expected:** Success flag "Created PROJ-123 (Sub-task)"
6. **Verify:** New Sub-task exists under the Story in Jira

### T1.14: CREATE_CHILD_ISSUE — Form Mode
1. Create a `CREATE_CHILD_ISSUE` button: parentIssueType = `Epic`, childIssueType = `Story`, mode = `form`, summary = `Story for {{issue.key}}`
2. Enable in a project, set visibilityCondition = `Epic`
3. Open an Epic issue, click the button
4. **Expected:** Inline quick-input form appears with summary pre-filled
5. Edit the summary if desired, click "Open Jira Screen"
6. **Expected:** Jira's native create screen opens in a new tab with issue type = Story and the edited summary pre-filled

### T1.15: Visibility Auto-Populate
1. Create a `CREATE_CHILD_ISSUE` button, enter parentIssueType = `Epic`
2. **Expected:** The "Visibility: Issue Types" field auto-populates to "Epic"

### T1.16: Appearance (Global Defaults)
1. In Global Settings, scroll to **Appearance**
2. Change **App Label** to "SmartOps", **Chooser Text** to "Pick an action", click **Save Appearance**
3. Open an issue panel → **Expected:** Heading shows "SmartOps Actions", subtitle shows "Pick an action"
4. Restore to "Cue" / "Choose Action" and save

---

## Test 2 — Project Settings

### T2.1: Category Grouping
1. Open **Project Settings → Cue** for a project
2. **Expected:** Buttons are grouped under their category headers

### T2.2: Toggle Category Off
1. Toggle a category off
2. Save, open an issue → **Expected:** All buttons in that category are hidden in all placements

### T2.3: Toggle Category On (auto-enables buttons)
1. Toggle the same category back on
2. **Expected:** All buttons in the category are toggled on in the list
3. Save, open an issue → **Expected:** All category buttons visible again

### T2.4: Per-Project Appearance
1. In Project Settings → Appearance section, set **App Label** = "Ops Center", **Chooser Text** = "Run an operation"
2. Save → **Expected:** Success message
3. Open an issue in that project → **Expected:** Panel heading shows "Ops Center Actions", subtitle "Run an operation"
4. Open an issue in a **different project** → **Expected:** Shows global defaults ("Cue Actions")

### T2.5: Toggle Individual Button
1. Disable a single button inside an enabled category
2. **Expected:** That specific button hidden; other buttons in the category still visible

### T2.6: Save Persistence
1. Toggle buttons/categories, save, navigate away and return
2. **Expected:** Toggle states preserved

### T2.7: Stale Reference Cleanup
1. Create a global button, enable it in a project
2. Delete the global button via Global Settings
3. Re-open Project Settings
4. **Expected:** Deleted button no longer appears

---

## Test 3 — Button Rendering

Filter logic (all must pass):
1. Category not disabled in project
2. `projectConfig.buttons[btn.id].enabled === true`
3. `btn.placements.includes(PLACEMENT)`
4. Visibility conditions match

### T3.1: Issue Panel
1. Enable a button with "panel" placement
2. Open an issue → **Expected:** Cue Actions panel shows horizontal button bar

### T3.2: Issue Panel — Category Accordion
1. Enable buttons from 2+ different categories
2. Open an issue → **Expected:** Each category shown as a collapsible section (default open) with its buttons inside

### T3.3: Issue Glance
1. Enable a button with "glance" placement
2. Open an issue → **Expected:** Cue glance widget in sidebar with count badge, buttons listed

### T3.4: Issue Action Menu
1. Enable a button with "action" placement
2. Open issue → click "..." menu → **Expected:** Cue items appear

### T3.5: Project Page
1. Enable a button with "page" placement
2. Open project → Cue page → **Expected:** Button grid with action type badges

### T3.6: Visibility Conditions
1. Create button with visibility issueTypes = "Bug", placement = panel
2. Open a Story issue → **Expected:** Button hidden
3. Open a Bug issue → **Expected:** Button visible

### T3.7: Unconfigured Project
1. Open issue in a project with no Cue config
2. **Expected:** No errors, null state rendered gracefully

### T3.8: Single Storage Read per Mount
1. Open browser dev tools → Network
2. Load an issue panel
3. **Expected:** Only one `invoke` call to `getButtons`, `getProjectConfig`, `getGlobalConfig`, and `getCategories` on mount

---

## Test 4 — Action Execution

### T4.1: OPEN_URL
1. Click button → **Expected:** New tab opens with tokens substituted in URL

### T4.2: OPEN_MODAL
1. Click button → **Expected:** Modal overlay appears with resolved URL

### T4.3: JIRA_TRANSITION
1. Click button with a valid transition ID
2. **Expected:** Issue status changes, success flag shown
3. Verify in issue history

### T4.4: JIRA_COMMENT
1. Click button → **Expected:** Comment posted with resolved template (check `{{user.displayName}}` and `{{date}}`)

### T4.5: JIRA_ASSIGN
1. Click button with valid account ID → **Expected:** Issue assignee changes

### T4.6: COPY_TEXT
1. Click button, paste into editor → **Expected:** Resolved template text in clipboard

### T4.7: SET_ISSUE_PROPERTY — Namespace
1. Create button: suffix = `test-status`, value = `verified`, type = `string`
2. Click button
3. **Verify via REST:**
   ```shell
   curl -u user:token \
     https://narendev.atlassian.net/rest/api/3/issue/DO-42/properties/cue.smartaction.test-status
   ```
   **Expected:** `{ "key": "cue.smartaction.test-status", "value": "verified" }`
4. Test with valueType = `number`: value = `42` → verify it's a number, not a string
5. Test with valueType = `boolean`: value = `true` → verify it's a boolean
6. Test with valueType = `json`: value = `{"level":"critical"}` → verify parsed object

### T4.8: FORGE_FUNCTION
1. Add a custom function to manifest.yml, click button → **Expected:** Function executes

### T4.9: Token Substitution
1. Use payload with `{{unknown.token}}` → **Expected:** Resolves to `[unknown token]`, no crash

### T4.10: Success/Error Flags
1. Successful action → **Expected:** Green auto-dismiss flag
2. Failed action (e.g. invalid transition ID) → **Expected:** Red persistent flag

### T4.11: No Double-Submit
1. Click a JIRA_COMMENT button, immediately click again while in-flight
2. **Expected:** Button disabled/loading during execution, second click ignored

### T4.12: CREATE_CHILD_ISSUE — Direct
1. Button: parentIssueType = `Story`, childIssueType = `Sub-task`, mode = `direct`, summary = `[{{issue.key}}]`
2. Open Story issue, click button
3. **Expected:** Success flag "Created PROJ-xyz (Sub-task)"
4. **Verify:** Sub-task created and linked under the Story

### T4.13: CREATE_CHILD_ISSUE — Form (sub-task)
1. Button: parentIssueType = `Story`, childIssueType = `Sub-task`, mode = `form`
2. Open Story issue, click button
3. **Expected:** Quick-input form appears with summary template pre-filled
4. Edit summary, click "Open Jira Screen"
5. **Expected:** Jira's `/secure/CreateSubTaskIssue!init.jspa` opens in new tab

### T4.14: CREATE_CHILD_ISSUE — Form (non-subtask)
1. Button: parentIssueType = `Epic`, childIssueType = `Story`, mode = `form`, summary = `Story from {{issue.key}}`
2. Open Epic issue, click button
3. **Expected:** Quick-input form with "Create Story" heading, summary template pre-filled
4. Click "Open Jira Screen"
5. **Expected:** Jira's `/secure/CreateIssueDetails!init.jspa` opens with project + issue type + summary pre-filled
6. Verify "Open Jira Screen" button is disabled when summary field is empty

### T4.15: CREATE_CHILD_ISSUE — Extra Fields
1. Create a direct-mode button with 1 extra field: label = "Priority", jiraField = "priority", type = "select", options = "High,Medium,Low"
2. Click from a matching issue
3. **Expected:** Quick-input form shows summary + Priority dropdown
4. Select "High", click Create
5. **Expected:** Child issue created with priority set to High

### T4.16: CREATE_CHILD_ISSUE — Wrong Parent Type
1. Button configured for Epic → Story but clicked on a Story issue
2. **Expected:** Error flag "This button creates a Story from an Epic, but the current issue is a Story"

---

## Test 5 — Last-Clicked Per Issue

### T5.1: Scoped Per Issue
1. Enable a button with `showLastClicked: true` on a panel placement
2. Click the button on issue PROJ-1
3. **Expected:** "Last: just now" shown below button on PROJ-1
4. Navigate to issue PROJ-2 (same project, same button enabled)
5. **Expected:** "Last: Never" on PROJ-2 — timestamps are independent

### T5.2: Persistence
1. Click button on issue PROJ-1, reload the page
2. **Expected:** Timestamp preserved ("Last: Xm ago" or similar)

### T5.3: Relative Time Formatting
1. Click button, wait 1–2 minutes, reload → **Expected:** "Xm ago"
2. After 1+ hour → **Expected:** "Xh ago"
3. After 1+ day → **Expected:** "Xd ago"

### T5.4: Project Page Tracking
1. Enable a button with `showLastClicked` on "page" placement
2. Click from Project Page, reload
3. **Expected:** Timestamp shown — tracked separately from issue-level clicks

---

## Test 6 — Property Key Migration

### T6.1: Existing buttons migrated on admin open
1. If any `SET_ISSUE_PROPERTY` buttons were saved before the namespace enforcement, open Global Settings
2. **Expected:** No errors; those buttons now have `cue.smartaction.` prefix in the property key (check by editing the button — the suffix field should show just the suffix without the prefix)
3. Click the button on an issue and verify via REST that the key used is `cue.smartaction.{suffix}`

### T6.2: Migration is idempotent
1. Close and re-open Global Settings multiple times
2. **Expected:** No duplicate prefixes (e.g. NOT `cue.smartaction.cue.smartaction.status`)

---

## Test 7 — Cross-Cutting

### T7.1: Storage Quota
```shell
forge usage
```
**Expected:** App stays well within Forge storage limits

### T7.2: Button Deletion Cleanup
1. Create button, enable in project, delete from Global Settings
2. Open Project Settings → **Expected:** Deleted button no longer appears

### T7.3: Category Deletion — Buttons Preserved
1. Create a category, assign buttons to it, delete the category
2. **Expected:** Buttons move to Uncategorised — none are deleted

---

## Test Result Template

| Test ID | Description | Pass/Fail | Notes |
|---------|-------------|-----------|-------|
| T1.1 | Categories — create | | |
| T1.2 | Categories — rename | | |
| T1.3 | Category accordion expand/collapse | | |
| T1.4 | Create button in category | | |
| T1.5 | Create all 9 types | | |
| T1.6 | SET_ISSUE_PROPERTY namespace in form | | |
| T1.7 | Edit button | | |
| T1.8 | Delete button | | |
| T1.9 | Delete category (buttons move to Uncategorised) | | |
| T1.10 | Inline validation | | |
| T1.11 | Custom success message | | |
| T1.12 | Last-clicked toggle + per-issue | | |
| T1.13 | CREATE_CHILD_ISSUE direct | | |
| T1.14 | CREATE_CHILD_ISSUE form | | |
| T1.15 | Visibility auto-populate | | |
| T1.16 | Global appearance defaults | | |
| T2.1 | Category grouping in project settings | | |
| T2.2 | Toggle category off — hides buttons | | |
| T2.3 | Toggle category on — auto-enables buttons | | |
| T2.4 | Per-project appearance override | | |
| T2.5 | Toggle individual button within category | | |
| T2.6 | Save persistence | | |
| T2.7 | Stale reference cleanup | | |
| T3.1 | Issue Panel render | | |
| T3.2 | Issue Panel category accordion | | |
| T3.3 | Issue Glance render | | |
| T3.4 | Issue Action render | | |
| T3.5 | Project Page render | | |
| T3.6 | Visibility conditions | | |
| T3.7 | Unconfigured project | | |
| T3.8 | Single storage read | | |
| T4.1 | OPEN_URL | | |
| T4.2 | OPEN_MODAL | | |
| T4.3 | JIRA_TRANSITION | | |
| T4.4 | JIRA_COMMENT | | |
| T4.5 | JIRA_ASSIGN | | |
| T4.6 | COPY_TEXT | | |
| T4.7 | SET_ISSUE_PROPERTY + cue.smartaction. prefix + REST verify | | |
| T4.8 | FORGE_FUNCTION | | |
| T4.9 | Token substitution | | |
| T4.10 | Success/Error flags | | |
| T4.11 | No double-submit | | |
| T4.12 | CREATE_CHILD_ISSUE direct | | |
| T4.13 | CREATE_CHILD_ISSUE form (sub-task) | | |
| T4.14 | CREATE_CHILD_ISSUE form (non-subtask) | | |
| T4.15 | CREATE_CHILD_ISSUE extra fields | | |
| T4.16 | CREATE_CHILD_ISSUE wrong parent | | |
| T5.1 | Last-clicked scoped per issue | | |
| T5.2 | Last-clicked persistence | | |
| T5.3 | Relative time formatting | | |
| T5.4 | Project page tracking | | |
| T6.1 | Property key migration on admin open | | |
| T6.2 | Migration idempotent | | |
| T7.1 | Storage quota | | |
| T7.2 | Button deletion cleanup | | |
| T7.3 | Category deletion — buttons preserved | | |