---
name: Storage Schema
description: > Last updated: v3.3.
model: claude-sonnet-4-5
---
# Cue — Storage Schema Documentation

> Last updated: v3.3.0

---

## Storage Keys

| Key | Type | Written By | Read By |
|-----|------|------------|---------|
| `smartactions:buttons` | `ButtonDef[]` | Global Admin UI | All render modules, project settings |
| `smartactions:categories` | `Category[]` | Global Admin UI | All render modules, project settings |
| `smartactions:project:{id}` | `ProjectConfig` | Project Settings UI | All render modules |
| `smartactions:global` | `GlobalConfig` | Global Admin UI | All render modules, admin UI |
| `smartactions:lastClicked:{buttonId}:{issueKey}` | `string` (ISO timestamp) | Dispatcher (fire-and-forget) | All issue render modules |
| `smartactions:version` | `string` | App bootstrap | Migration checks |

> **Last-clicked key is scoped per issue.** Each button tracks its own timestamp separately per Jira issue key. Clicking a button on PROJ-1 does not affect the timestamp shown on PROJ-2.
>
> Project page (`jira:projectPage`) has no issue context — it uses an empty string for `issueKey`, giving it its own separate tracking slot.

---

## Constants

```typescript
export const CATEGORIES_KEY = 'smartactions:categories';
export const GLOBAL_KEY = 'smartactions:global';
export const LAST_CLICKED_PREFIX = 'smartactions:lastClicked:';

// All SET_ISSUE_PROPERTY keys are stored and written with this prefix.
// User types just the suffix; app stores "cue.smartaction.{suffix}".
// JQL: issue.property[cue.smartaction.status].value = "escalated"
// TODO (Phase 2 - nice to have): add jira:entityPropertyIndex in manifest.yml
// for indexed fast JQL search.
export const PROPERTY_KEY_PREFIX = 'cue.smartaction.';
```

---

## TypeScript Interfaces

### ActionType
```typescript
type ActionType =
  | 'OPEN_URL'
  | 'OPEN_MODAL'
  | 'JIRA_TRANSITION'
  | 'JIRA_COMMENT'
  | 'JIRA_ASSIGN'
  | 'COPY_TEXT'
  | 'SET_ISSUE_PROPERTY'
  | 'FORGE_FUNCTION'
  | 'CREATE_CHILD_ISSUE';
```

### PlacementType
```typescript
type PlacementType = 'panel' | 'glance' | 'action' | 'page';
```

### ButtonStyle
```typescript
type ButtonStyle = 'primary' | 'secondary' | 'danger';
```

### Category
```typescript
interface Category {
  id: string;   // cat_<timestamp>_<random>
  name: string; // display name
}
```

### ButtonDef
```typescript
interface ButtonDef {
  id: string;                            // Unique ID (btn_<timestamp>_<random>)
  label: string;                         // Display label (max 40 chars)
  icon: string;                          // Icon token or emoji
  style: ButtonStyle;
  actionType: ActionType;
  actionPayload: Record<string, string>; // Action-specific fields (all values are strings)
  visibilityCondition?: {
    issueTypes?: string[];               // Filter by issue type name (e.g. "Epic", "Bug")
    statusCategories?: string[];         // Filter by status category name
  };
  placements?: PlacementType[];          // Which placements to show in (default: ['panel'])
  successMessage?: string;               // Custom message shown after successful execution
  showLastClicked?: boolean;             // Show relative timestamp per issue after click
  createdAt: string;                     // ISO 8601 creation timestamp
  categoryId?: string;                   // ID of the Category this button belongs to (optional)
}
```

> `placements` is set **per-button globally** in Global Settings. It is NOT per-project.
> Render components filter by `btn.placements.includes(PLACEMENT)`, defaulting to `['panel']` when undefined.

> `categoryId` links to a `Category.id`. If the category is disabled for a project, all buttons with that `categoryId` are hidden in that project.

### CreateChildIssuePayload
Stored as flat string values inside `ButtonDef.actionPayload`:

```typescript
// Fields stored in actionPayload (all values are strings)
{
  mode: 'direct' | 'form';
  parentIssueType: string;       // e.g. "Epic" — must match visibilityCondition.issueTypes[0]
  childIssueType: string;        // e.g. "Story", "Sub-task", "Initiative"
  summary: string;               // supports tokens e.g. "[{{issue.key}}] {{issue.summary}}"
  description?: string;          // optional, supports tokens
  assignToMe?: 'true' | 'false'; // assign created child to current user
  copyLabels?: 'true' | 'false'; // copy labels from parent issue
  useSubtaskHierarchy?: 'true' | 'false'; // true = fields.parent (native); false = issue link
  // Extra fields at click time (up to 3):
  efCount?: string;              // number of extra fields, e.g. "2"
  ef0_label?: string;            // display label for extra field 0
  ef0_jiraField?: string;        // Jira field key for extra field 0
  ef0_type?: 'text' | 'select';  // input type for extra field 0
  ef0_options?: string;          // comma-separated options (when type === 'select')
  // ef1_*, ef2_* follow the same pattern
}
```

### ExtraFieldDef
```typescript
interface ExtraFieldDef {
  label: string;          // display label in quick-input form
  jiraField: string;      // Jira field key, e.g. "priority", "customfield_10001"
  type: 'text' | 'select';
  options: string;        // comma-separated options (used when type === 'select')
}
```

Helper: `parseExtraFieldDefs(actionPayload)` returns `ExtraFieldDef[]` from flat payload keys.

### ProjectButtonConfig
```typescript
interface ProjectButtonConfig {
  enabled: boolean;
}
```

### ProjectConfig
```typescript
interface ProjectConfig {
  buttons: Record<string, ProjectButtonConfig>; // keyed by ButtonDef.id
  appLabel?: string;    // overrides GlobalConfig.appLabel for this project
  chooserText?: string; // overrides GlobalConfig.chooserText for this project
  categories?: Record<string, { enabled: boolean }>; // keyed by Category.id
}
```

> `categories` — if a category entry has `enabled: false`, all buttons with that `categoryId` are hidden in this project, regardless of individual button toggles. Missing entry = enabled.

### GlobalConfig
```typescript
interface GlobalConfig {
  allowedProjectIds: string[];   // empty = all projects allowed
  appLabel?: string;             // default 'Cue'
  chooserText?: string;          // default 'Choose Action'
  accentColor?: 'blue' | 'green' | 'purple' | 'teal' | 'red'; // default 'blue'
}
```

### VisibilityCondition
```typescript
interface VisibilityCondition {
  issueTypes?: string[];        // e.g. ["Epic", "Story"]
  statusCategories?: string[];  // e.g. ["To Do", "In Progress"]
}
```

---

## Action Payload Fields

| Action Type | Required Fields | Optional Fields |
|-------------|----------------|-----------------|
| `OPEN_URL` | `url` | — |
| `OPEN_MODAL` | `url` | — |
| `JIRA_TRANSITION` | `transitionId` | — |
| `JIRA_COMMENT` | `commentTemplate` | — |
| `JIRA_ASSIGN` | `accountId` | — |
| `COPY_TEXT` | `copyTemplate` | — |
| `SET_ISSUE_PROPERTY` | `propertyKey` (suffix only in form; stored as `cue.smartaction.{suffix}`), `propertyValue`, `valueType` | — |
| `FORGE_FUNCTION` | `functionName` | — |
| `CREATE_CHILD_ISSUE` | `parentIssueType`, `childIssueType`, `summary`, `mode` | `description`, `assignToMe`, `copyLabels`, `useSubtaskHierarchy`, `efCount`, `ef0_*`…`ef2_*` |

---

## Supported Tokens

| Token | Resolves To |
|-------|-------------|
| `{{issue.key}}` | Current issue key (e.g. DO-42) |
| `{{issue.summary}}` | Issue title text |
| `{{issue.status}}` | Current status name |
| `{{issue.type}}` | Issue type name |
| `{{project.key}}` | Project key |
| `{{user.displayName}}` | Logged-in user display name |
| `{{date}}` | Today's date in YYYY-MM-DD format |

Unknown tokens resolve to `[unknown token]` — no crash, no silent data loss.

---

## Resolver Endpoints

All endpoints are invoked from the frontend via `@forge/bridge` `invoke()`.

### Storage CRUD

| Endpoint | Payload | Returns | Description |
|----------|---------|---------|-------------|
| `getButtons` | — | `ButtonDef[]` | Load all global buttons |
| `saveButtons` | `{ buttons: ButtonDef[] }` | `void` | Persist full button list |
| `deleteButton` | `{ buttonId: string }` | `void` | Remove button by ID |
| `getProjectConfig` | `{ projectId: string }` | `ProjectConfig` | Load project config |
| `saveProjectConfig` | `{ projectId, config }` | `void` | Save project config |
| `getGlobalConfig` | — | `GlobalConfig` | Load global config |
| `saveGlobalConfig` | `{ config: GlobalConfig }` | `void` | Save global config |
| `getCategories` | — | `Category[]` | Load all categories |
| `saveCategories` | `{ categories: Category[] }` | `void` | Persist full category list |
| `getVersion` | — | `string` | Get schema version |
| `setVersion` | `{ version: string }` | `void` | Set schema version |

### Last-Clicked

| Endpoint | Payload | Returns | Description |
|----------|---------|---------|-------------|
| `getLastClickedMap` | `{ buttonIds: string[], issueKey: string }` | `Record<string, string>` | Get last-clicked timestamps scoped per issue |
| `recordLastClicked` | `{ buttonId: string, issueKey: string }` | `void` | Record ISO timestamp for button click on specific issue |

### Jira API Helpers

| Endpoint | Payload | Returns | Description |
|----------|---------|---------|-------------|
| `listJiraProjects` | — | `JiraProject[]` | Fetch all projects from Jira REST API |
| `createChildIssue` | See below | `{ success, issueKey?, message? }` | Create a child issue via REST API (direct mode) |
| `resolveChildCreateInfo` | `{ parentKey, projectKey, childIssueType }` | `ChildCreateInfo \| { error }` | Resolve numeric IDs for building Jira create URL (form mode) |

### Migrations

| Endpoint | Payload | Returns | Description |
|----------|---------|---------|-------------|
| `migratePropertyKeys` | — | `void` | One-time migration: rewrites all SET_ISSUE_PROPERTY buttons to use `cue.smartaction.{suffix}` namespace. Idempotent — no-ops if already namespaced. Called on every Global Settings mount. |

#### `createChildIssue` payload
```typescript
{
  parentKey: string;
  projectKey: string;
  childIssueType: string;
  summary: string;
  description?: string;
  assignToMe?: boolean;
  copyLabels?: boolean;
  useSubtaskHierarchy?: boolean; // true = fields.parent; false = issue link
  extraFields?: { jiraField: string; type: 'text' | 'select'; value: string }[];
}
```

#### `resolveChildCreateInfo` response
```typescript
// Success:
{
  projectId: string;    // Jira numeric project ID
  issueTypeId: string;  // Jira numeric issue type ID
  parentId: string;     // Jira numeric parent issue ID
  isSubtask: boolean;   // Whether the child type is a native sub-task
}
// Error:
{ error: string }
```

---

## Button Filter Logic (all placements)

A button is shown in a placement only when **all** pass:

```
1. projConfig.categories?.[btn.categoryId]?.enabled !== false   (category gate)
2. projConfig.buttons[btn.id]?.enabled === true                  (project toggle)
3. btn.placements.includes(PLACEMENT)                            (placement gate)
4. isVisible(btn, issueType, statusCategory)                     (visibility conditions)
```

Category gate: if the entry is missing (undefined), the category is treated as **enabled**. Only an explicit `false` hides buttons.

---

## Storage Access Rules

1. All storage access must go through `src/storage/client.ts`
2. Never call `storage.get()` or `storage.set()` directly from components
3. Always handle null returns with `?? []` or `?? {}`
4. One `storage.get()` per component mount only — cache result in state
5. Use `@forge/storage` Entity Store exclusively — no external DB
6. `recordLastClicked` must always be fire-and-forget — never awaited in the dispatcher

---

## Client Functions (`src/storage/client.ts`)

| Function | Signature | Description |
|----------|-----------|-------------|
| `getButtons()` | `() => Promise<ButtonDef[]>` | Load all global buttons |
| `saveButtons(buttons)` | `(ButtonDef[]) => Promise<void>` | Persist full button list |
| `deleteButton(buttonId)` | `(string) => Promise<void>` | Remove button by ID |
| `getProjectConfig(projectId)` | `(string) => Promise<ProjectConfig>` | Load project config |
| `saveProjectConfig(projectId, config)` | `(string, ProjectConfig) => Promise<void>` | Save project config |
| `getGlobalConfig()` | `() => Promise<GlobalConfig>` | Load global config |
| `saveGlobalConfig(cfg)` | `(GlobalConfig) => Promise<void>` | Save global config |
| `getCategories()` | `() => Promise<Category[]>` | Load all categories |
| `saveCategories(cats)` | `(Category[]) => Promise<void>` | Persist full category list |
| `getLastClickedMap(buttonIds, issueKey)` | `(string[], string) => Promise<Record<string, string>>` | Get last-clicked map scoped per issue |
| `recordLastClicked(buttonId, issueKey)` | `(string, string) => Promise<void>` | Record click timestamp per issue |
| `getVersion()` | `() => Promise<string>` | Get schema version |
| `setVersion(version)` | `(string) => Promise<void>` | Set schema version |

---

## Manifest Permissions

| Scope | Required For |
|-------|-------------|
| `read:jira-work` | Read issue fields, type, status, project, labels, issue IDs |
| `read:jira-user` | `GET /rest/api/3/myself` for assign-to-me feature |
| `write:jira-work` | Transition, comment, assign, issue properties, create issues, issue links |
| `manage:jira-project` | Access project settings module |
| `storage:app` | Forge Entity Store for button/project/category config |